# Simili: Project Overview & Core Features
Last Updated: September 23, 2025

## 1. Project Vision & Core Philosophy
**Vision:** To create a scalable, equitable math learning environment where every child can be heard, supported, and challenged. Simili aims to establish a new paradigm for math learning technology—one where student voice is the curriculum, and AI amplifies teacher insight into how children think.

**Core Philosophy:** Simili is an AI-powered, voice-first learning platform designed to help K-8 students build deep conceptual understanding of mathematics. It is built on four pedagogical principles:

**Create Intellectual Need:** We first present a perplexing situation so the student feels a genuine need for mathematics to resolve it. Key information is withheld until the student identifies the need for it.

**Prioritize Productive Struggle:** The cognitive work of grappling with a problem is where deep learning occurs. We provide open-ended tools that encourage student thinking, not menus that give away the solution path.

**Make Meaning First, Formalize Last:** Abstract mathematical concepts are more durable when grounded in a student's own actions and discoveries. Formal vocabulary and notation are only introduced in Act 3, after intuitive understanding is built.

**Student Talk Drives Learning:** The AI's primary role is to act as an expert tutor that makes student reasoning visible, provides timely scaffolds, and guides them toward metacognition.

### 1.1 Target Platforms
**Version 1 (V1):** Web Application (optimized for desktop and tablet browsers).

**Future Versions:** Native mobile/tablet applications (iOS and Android).

## 2. Jobs to be Done (JTBD)
This application serves the following core student needs:

**Explore:** When I see a new problem, I want to explore it with my voice and curiosity before being told what to do, so I can connect it to what I already know.

**Experiment:** When I have an idea, I want to say my plan out loud and use tools to test it in a low-stakes environment, so I can learn by doing.

**Persevere:** When I'm stuck, I want to get a small hint that helps me think—not one that gives away the answer—so I can build the confidence to solve it myself.

**Formalize:** When I solve a problem, I want to learn the official math words and symbols for what I did, so I can communicate my ideas like a mathematician.

## 3. Core Features & User Flow: The Three-Act Task
The primary user experience is a single, unified learning interface guided by the AI tutor, Pi. This interface consists of several key components: the Visual Pane, an Avatar of Pi, a Live Chat Transcript, an Interactive Canvas, and a Toolbox. The learning journey unfolds across three distinct acts.

### Act 1: Visual Hook & Wonder
The goal is to spark curiosity and elicit the student's initial ideas.

**User Flow:** A perplexing, math-rich animation (the Animated Visual Hook) is presented in the Visual Pane. Pi prompts the student with an open-ended question ("What do you notice? What do you wonder?"). The student responds verbally, and their thoughts are captured via Open-Ended Voice Capture and displayed in the transcript. The conversation naturally leads to a core mathematical question. Pi may then ask the student to use a tool to make an initial estimate on the Interactive Canvas.

### Act 2: Voice-First Problem Solving & The Brownie Lab
This is the core of the experience, where students experiment and grapple with the problem.

**User Flow:** Pi presents the formal problem ("Partition the brownie for 3 friends"). The student can access a set of context-specific tools from the Toolbox.

They use the Canvas Slice Tool to draw partitions on the brownie.

To check their work, they press the Equality Check Button, which provides instant visual feedback (coloring the pieces green or red).

The Canvas Undo/Eraser allows for easy revision.

If the student is inactive or struggling, the stateful AI provides a targeted scaffolding prompt.

Once a solution is reached, a "Twist" Event (e.g., a fourth friend arrives) can be triggered to deepen the learning and challenge the student to adapt their strategy.

### Act 3: Synthesis & Formalization
The goal is to consolidate the student's understanding and connect it to formal mathematical language.

**User Flow:** The student's correct solution is validated with a Solution Reveal Animation, which can Overlay their own work to confirm their success. Pi then initiates a consolidation dialogue.

Key terms are introduced using Animated Vocabulary and are highlighted in the transcript.

The student demonstrates their understanding through a final Drag-and-Drop Labeling activity on the canvas.

A Conditional "Challenge" Button appears, offering an optional extension for advanced learners.

## 4. Proposed Data Model (Initial Thoughts)
To support this experience, we'll need to model the following core entities:

**User:** Represents a student account.

**Lesson:** Contains the configuration for a specific Three-Act Task (e.g., the visual hooks, required tools, solution logic).

**Session:** Represents a single student's attempt at a lesson from start to finish.

**TranscriptEntry:** A single utterance from either the student or Pi, stored as part of a Session.

**CanvasState:** A snapshot of the student's work on the canvas, saved at key moments within a Session.

## 5. Out of Scope for V1
The initial build will focus exclusively on delivering a high-quality, single-player lesson experience. The following features will be considered for future versions:

- Teacher/Admin dashboards
- Student accounts and long-term progress tracking
- A full library of lessons
- Classroom management features