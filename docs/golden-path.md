# The Golden Path: Simili's Data Flow Architecture

## High-Level Overview: The Data Journey 🗺️
Here is the step-by-step journey of data from our Supabase database to the student's screen:

1. **UI Layer (React Component):** A screen needs data to render (e.g., the lesson page needs the lesson content).

2. **Hook Layer (Custom Hook):** The component calls a custom React Hook (e.g., useLesson) that we'll write. This hook handles the logic of when and how to fetch the data.

3. **Service Layer (Service Function):** The hook calls a dedicated, async "service" function whose only job is to communicate with Supabase.

4. **Backend (Supabase):** The service function uses the Supabase client to make a request to the database. Supabase finds the data and returns it.

5. **Return Trip:** The data is returned from Supabase back to the service function, then to the hook, which updates the state of the UI component.

6. **UI Renders:** The component now has the data it needs and displays it to the student.

## A Practical Example: Loading "The Perplexing Brownie"
Let's walk through exactly what happens when a student clicks on a lesson.

### Step 1: The Route and UI Component
The student navigates to a URL like `/lessons/the-perplexing-brownie`. Our Next.js router loads the `page.tsx` component for that route. This component knows it needs data for a specific lesson, but it doesn't fetch it directly. Instead, it calls our custom hook.

```typescript
// in app/(lessons)/[lessonId]/page.tsx

import { useLesson } from '@/lib/hooks/useLesson';

export default function LessonPage({ params }) {
  const { lessonId } = params;
  const { data: lesson, isLoading, error } = useLesson(lessonId);

  if (isLoading) return <div>Loading Lesson...</div>;
  if (error) return <div>Error loading lesson.</div>;

  return (
    <div>
      <h1>{lesson.title}</h1>
      {/* We would render the actual lesson components here */}
    </div>
  );
}
```

### Step 2: The Custom Hook (useLesson)
This hook, which we'll create in `lib/hooks/`, is the middleman. It takes the `lessonId`, manages the loading and error states, and calls the service layer to actually get the data.

For advanced apps, this is where you'd use a library like TanStack Query for caching, but for now, a simple `useEffect` hook illustrates the pattern.

```typescript
// in lib/hooks/useLesson.ts

import { useState, useEffect } from 'react';
import { getLessonById } from '@/lib/services/lessonService';

export const useLesson = (lessonId: string) => {
  const [data, setData] = useState(null);
  const [isLoading, setIsLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchLesson = async () => {
      try {
        const lessonData = await getLessonById(lessonId);
        setData(lessonData);
      } catch (err) {
        setError(err);
      } finally {
        setIsLoading(false);
      }
    };

    if (lessonId) {
      fetchLesson();
    }
  }, [lessonId]);

  return { data, isLoading, error };
};
```

### Step 3: The Service Function (getLessonById)
This is the only part of our code that should directly talk to Supabase. It's a simple, async function that takes an ID, builds a query, and returns the data. This keeps all our Supabase logic clean and in one place.

```typescript
// in lib/services/lessonService.ts

import { supabase } from '@/lib/supabase'; // Our configured Supabase client

export const getLessonById = async (lessonId: string) => {
  const { data, error } = await supabase
    .from('lessons') // The name of our table
    .select('*')     // Get all columns
    .eq('id', lessonId) // Where the id matches
    .single(); // We only expect one result

  if (error) {
    throw new Error(error.message);
  }

  // The lesson_content field will contain our full lesson JSON
  return data;
};
```

This pattern—**Component → Hook → Service**—is our Golden Path. We will reuse it for everything: fetching user profiles, saving session data, getting transcript entries, etc. It's clean, easy to test, and scalable.