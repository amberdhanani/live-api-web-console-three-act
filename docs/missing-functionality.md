# Simili: Missing Functionality Analysis

*Generated: September 27, 2025*

This document catalogs all the functionality that Simili is supposed to have according to the project documentation but doesn't currently exist. The current codebase is a Google GenAI live API console that needs to be transformed into the Simili math learning platform.

## Technical Infrastructure

### Backend & Database Setup
- [ ] **Supabase Project Setup** - Create and configure Supabase project
- [ ] **Database Schema Implementation** - Create users, lessons, sessions, transcript_entries tables
- [ ] **Supabase Client Configuration** - Set up and configure Supabase client in Next.js
- [ ] **Authentication System** - Implement Supabase Auth integration
- [ ] **Real-time Subscriptions** - Set up real-time data sync for sessions/transcripts

### Framework Migration
- [ ] **Next.js Migration** - Convert from Create React App to Next.js with App Router
- [ ] **File Structure Reorganization** - Implement proper Next.js app/ directory structure
- [ ] **Route Groups Setup** - Create (auth) and (lessons) route groups
- [ ] **Dynamic Routes** - Implement [lessonId] dynamic routing
- [ ] **Tailwind CSS Integration** - Replace current styling with Tailwind CSS

### Data Layer & Golden Path
- [ ] **Service Layer Creation** - Build lib/services/ functions for Supabase operations
- [ ] **Custom Hooks Layer** - Create lib/hooks/ for data fetching patterns
- [ ] **Type Definitions** - Define TypeScript types for all data models
- [ ] **Golden Path Implementation** - Enforce UI → Hooks → Services → Supabase pattern

### AI Integration
- [ ] **Speech-to-Text Pipeline** - Integrate Google Gemini API for voice transcription
- [ ] **AI Tutor Logic System** - Implement stateful AI tutor (Pi) using Gemini/Claude
- [ ] **Real-time Voice Processing** - Set up continuous voice capture and processing
- [ ] **AI Response Generation** - Create context-aware tutor response system

### Canvas Infrastructure
- [ ] **Canvas Library Integration** - Integrate Konva.js or Paper.js for interactive drawing
- [ ] **Canvas State Management** - Implement canvas state persistence and restoration
- [ ] **Tool System Architecture** - Create extensible tool system for canvas interactions
- [ ] **Undo/Redo System** - Implement canvas action history and reversal

### Performance & Optimization
- [ ] **Component Architecture** - Separate UI components (components/ui/) from core components (components/core/)
- [ ] **State Management** - Implement proper state management for complex lesson flows
- [ ] **Error Handling** - Add comprehensive error handling and user feedback
- [ ] **Loading States** - Implement loading states for async operations

## User-Facing Features

### Core Learning Interface
- [ ] **Visual Pane Component** - Container for animated visual hooks and lesson content
- [ ] **Pi Avatar Component** - AI tutor visual representation with animations
- [ ] **Live Chat Transcript** - Real-time conversation display with student/Pi differentiation
- [ ] **Interactive Canvas** - Main drawing/interaction surface for student work
- [ ] **Toolbox Component** - Context-sensitive tool selection interface

### Act 1: Visual Hook & Wonder
- [ ] **Animated Visual Hook System** - Perplexing math-rich animations to spark curiosity
- [ ] **Open-Ended Voice Capture** - "What do you notice? What do you wonder?" interaction
- [ ] **Initial Estimation Tools** - Canvas tools for student's first attempts
- [ ] **Wonder Question Generation** - AI-driven question formulation from student responses

### Act 2: Voice-First Problem Solving
- [ ] **Brownie Lab Environment** - Specific problem context with visual brownie representation
- [ ] **Canvas Slice Tool** - Draw partitions/divisions on visual objects
- [ ] **Equality Check System** - Instant visual feedback (green/red piece coloring)
- [ ] **Canvas Undo/Eraser Tools** - Easy revision and mistake correction
- [ ] **Stateful AI Scaffolding** - Context-aware hints when student is stuck or inactive
- [ ] **Twist Event System** - Dynamic problem modifications (e.g., "fourth friend arrives")
- [ ] **Inactivity Detection** - Monitor student engagement and provide timely prompts

### Act 3: Synthesis & Formalization
- [ ] **Solution Reveal Animation** - Validate correct solutions with visual confirmation
- [ ] **Solution Overlay System** - Show correct solution overlaid on student work
- [ ] **Consolidation Dialogue** - AI-guided reflection and understanding check
- [ ] **Animated Vocabulary System** - Interactive introduction of mathematical terms
- [ ] **Transcript Highlighting** - Highlight key terms and concepts in conversation history
- [ ] **Drag-and-Drop Labeling** - Final assessment activity on canvas
- [ ] **Conditional Challenge Button** - Optional extension problems for advanced learners

### Voice & Audio Processing
- [ ] **Continuous Voice Capture** - Always-on microphone with smart activation
- [ ] **Real-time Transcription Display** - Live speech-to-text in transcript
- [ ] **Voice Activity Detection** - Automatic start/stop of transcription
- [ ] **Audio Quality Indicators** - Visual feedback for microphone/audio issues
- [ ] **Multi-turn Conversation Flow** - Natural back-and-forth dialogue management

### Lesson Management
- [ ] **Lesson Loading System** - Fetch and initialize lesson configurations
- [ ] **Session State Persistence** - Save and restore student progress
- [ ] **Progress Tracking** - Track completion of each act and overall lesson
- [ ] **Session Resumption** - Allow students to continue from where they left off

### Visual & Animation Systems
- [ ] **Mathematical Animations** - Visual representations of math concepts
- [ ] **Transition Animations** - Smooth movement between acts and states
- [ ] **Feedback Animations** - Visual responses to student actions
- [ ] **Loading Animations** - Engaging content while processing

### Accessibility & UX
- [ ] **Keyboard Navigation** - Full keyboard accessibility for all interactions
- [ ] **Screen Reader Support** - Proper ARIA labels and announcements
- [ ] **Mobile Responsiveness** - Tablet and mobile-optimized interface
- [ ] **Error State Handling** - User-friendly error messages and recovery options
- [ ] **Offline Capability** - Basic functionality when internet is intermittent

### Assessment & Validation
- [ ] **Solution Validation Logic** - Determine correctness of student canvas work
- [ ] **Partial Credit System** - Recognize partially correct approaches
- [ ] **Misconception Detection** - Identify common mathematical errors
- [ ] **Adaptive Difficulty** - Adjust challenge level based on student performance

## Implementation Priority

### Phase 1: Foundation (Weeks 1-2)
- Next.js migration and project structure
- Supabase setup and basic authentication
- Core component architecture (Visual Pane, Avatar, Transcript, Canvas)

### Phase 2: Core Learning Flow (Weeks 3-4)
- Basic three-act structure implementation
- Voice capture and AI integration
- Canvas drawing tools and basic interactions

### Phase 3: Enhanced Features (Weeks 5-6)
- Advanced AI scaffolding and tutoring logic
- Animation systems and visual feedback
- Assessment and validation systems

### Phase 4: Polish & Optimization (Weeks 7-8)
- Accessibility improvements
- Performance optimization
- Error handling and edge cases