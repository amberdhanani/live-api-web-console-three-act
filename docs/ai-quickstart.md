# AI Agent Quickstart Guide: Simili

## Project Summary
Simili is a voice-first, AI-powered math learning platform for K-8 students. The application is a full-stack web app built with a Next.js frontend and a Supabase backend. The core user experience is a three-act task framework that emphasizes student talk and productive struggle, guided by an AI tutor named Pi.

## Key Technologies
- **Backend & Database:** Supabase (PostgreSQL, Auth, Real-time)
- **Frontend Framework:** Next.js (using the App Router)
- **Language:** TypeScript
- **Styling:** Tailwind CSS
- **AI Services:** Google Gemini API (for Speech-to-Text and/or Tutor Logic)

## Project Structure Overview
```
simili-app/
├── app/                  # Main application folder (routing)
│   └── [lessonId]/       # Dynamic route for lessons
├── components/           # Shared, reusable React components
│   └── ui/               # Simple UI elements (buttons, etc.)
│   └── core/             # Complex components (Canvas, Chat)
├── lib/                  # Helper functions, hooks, and services
│   └── hooks/            # Custom React hooks
│   └── services/         # Supabase client functions
└── tailwind.config.ts    # Tailwind CSS configuration
```

## Development Commands
- `npm run dev` - Starts the development server.
- `npm run build` - Builds the application for production.
- `npm run start` - Starts the production server.

## Best Practices Established (The Golden Path)
**This is the most important section. All generated code must follow these rules.**

### Data Fetching Follows the Golden Path:
All communication with the Supabase backend must follow this pattern:

1. **UI Components** (in `app/` or `components/`) should NEVER call Supabase directly.
2. **Components** call custom hooks from `lib/hooks/`.
3. **Custom hooks** call service functions from `lib/services/`.
4. **Service functions** are the ONLY files that should import and use the Supabase client.

### Component Organization:
- **Simple, reusable UI elements** (a styled button, a modal frame) go in `components/ui/`.
- **Complex, stateful components** that are core to the Simili experience (like the entire interactive LessonCanvas or the ChatTranscript display) go in `components/core/`.

### Type Safety First:
Always use TypeScript. Define custom types for all data models (e.g., Lesson, Session) in a `types/` directory or alongside the relevant service.

### Use Supabase for All Backend Needs:
Do not create a separate server. User authentication, database queries, and other backend tasks should all be handled through the Supabase client.

## Quick Start Checklist for Claude
Before writing code, review:

1. `docs/project-overview.md` for the project's vision and user experience.
2. `docs/technical-guide.md` for the detailed architecture and data models.
3. `docs/golden-path.md` for the required data-fetching pattern.

## Planning Complete! What's Next?
Congratulations! We have now created all four of our foundational documents. This is a massive step and sets you up for a successful build.

The planning phase is over, and now the building phase begins. Here are the logical next steps:

1. **Project Setup:** Initialize a new Next.js with Tailwind CSS project on your local machine.
2. **Backend Setup:** Create a new project on Supabase and use the "Data Architecture" from our guide to create the users, lessons, sessions, and transcript_entries tables.
3. **Connect the Two:** Install the Supabase client in your Next.js app and configure it to connect to your new Supabase project.
4. **Implement the First Golden Path:** Create the very first end-to-end feature, like fetching and displaying a single lesson from your Supabase database.