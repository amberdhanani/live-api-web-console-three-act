# Simili: Technical Guide (Final)

## 1. Architecture Overview
Simili will use a modern full-stack architecture with a Next.js frontend and a Supabase backend. The core principle is a clear separation of concerns, where the user interface (UI) fetches and displays data from the backend, which manages the database and user authentication.

The data flow will follow a pattern we'll call the "Golden Path," where UI components use custom hooks to securely request data from Supabase, ensuring all data is validated and state is managed cleanly.

## 2. Tech Stack
| Category | Technology | Purpose |
|----------|------------|---------|
| Frontend Framework | Next.js (React) | The foundation for our application, providing file-based routing, server components, and a robust development environment. |
| Language | TypeScript | Ensures type safety across the entire project, reducing bugs and improving developer experience. |
| Styling | Tailwind CSS | A utility-first CSS framework for rapid and consistent UI development. |
| Backend & Database | Supabase | Our all-in-one backend. Provides a PostgreSQL database, user authentication, and real-time capabilities. |
| Interactive Canvas | Konva.js or Paper.js | A dedicated library for managing the complex drawing interactions on the lesson canvas. |
| AI - Speech-to-Text | Google Gemini API | For real-time transcription of student audio. |
| AI - Tutor Logic | Google Gemini or Claude API | The LLM "brain" for the AI tutor, Pi. |

## 3. Project Structure (Next.js with Tailwind)
We will organize the project using the standard Next.js app/ directory structure.

```
simili-app/
├── app/                  # Main application folder
│   ├── (auth)/           # Route group for login, signup pages
│   ├── (lessons)/        # Route group for lesson pages
│   │   └── [lessonId]/   # Dynamic route for a specific lesson
│   │       └── page.tsx  # The main lesson component
│   ├── globals.css       # Global styles for Tailwind CSS
│   ├── layout.tsx        # Main layout of the application
│   └── page.tsx          # The homepage
├── components/           # Shared, reusable React components
│   └── ui/               # Simple UI elements (buttons, modals)
│   └── core/             # Complex components (e.g., The Canvas)
├── lib/                  # Helper functions, utility code
│   └── supabase.ts       # Supabase client configuration
│   └── hooks/            # Custom React hooks (e.g., useLessonData)
├── public/               # Static assets (images, fonts)
├── tailwind.config.ts    # Configuration file for Tailwind CSS
└── package.json          # Project dependencies
```

## 4. Data Architecture (Supabase)
Our database will be designed around a few core tables in Supabase.

### users
Manages user data, extending Supabase's built-in auth.users table.

**Columns:** id (FK to auth.users), full_name, avatar_url, created_at.

### lessons
Stores the content and configuration for each lesson.

**Columns:** id, title, grade_level, created_at, lesson_content (JSONB).

### sessions
Tracks a single student's attempt at a specific lesson.

**Columns:** id, user_id (FK to users), lesson_id (FK to lessons), started_at, completed_at, final_canvas_state (JSONB).

### transcript_entries
Stores every line of dialogue from a session.

**Columns:** id, session_id (FK to sessions), speaker ("student" or "pi"), text_content, timestamp.