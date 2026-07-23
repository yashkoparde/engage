# 🚀 Engage — Real-Time Interactive Classroom Engagement Platform

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![React 18](https://img.shields.io/badge/React-18-61DAFB?logo=react)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?logo=typescript)](https://www.typescriptlang.org/)
[![Vite](https://img.shields.io/badge/Vite-5.0-646CFF?logo=vite)](https://vitejs.dev/)
[![Supabase](https://img.shields.io/badge/Supabase-Realtime-3ECF8E?logo=supabase)](https://supabase.com/)
[![TailwindCSS](https://img.shields.io/badge/TailwindCSS-3.4-38B2AC?logo=tailwind-css)](https://tailwindcss.com/)

**Engage** is a unified real-time gamification and interactive learning platform that synchronizes teacher presentations with student devices. It transforms classroom lectures into live interactive sessions featuring real-time quizzes, 3D concept flashcards, competitive typing arenas, crowd-sourced Q&A forums, and instant comprehension pacing checks.

---

## 🏛️ Monorepo Architecture

```
engage/
├── apps/
│   ├── faculty/                 # 🎓 Teacher / Instructor Orchestration Portal
│   │   ├── src/
│   │   │   ├── components/      # CircularMenu, PollsManager, SpeedTyper, FlashcardsArena, QAArena
│   │   │   ├── lib/supabase.ts  # Realtime channel broadcast engine
│   │   │   └── App.tsx          # Multi-stage presentation controller
│   │   └── package.json
│   └── student/                 # 📱 Student Companion Client
│       ├── src/
│       │   ├── components/      # CircularTimer, ConfusionView, LeaderboardView, Splash, StudentView
│       │   ├── lib/supabase.ts  # Realtime student sync & offline queue
│       │   └── App.tsx          # Dynamic activity renderer
│       ├── server.ts            # Standalone Node/Socket backend server
│       ├── supabase_schema.sql  # Database schema, indexes & RLS policies
│       └── package.json
├── package.json                 # Root monorepo workspace scripts
├── docker-compose.yml           # Local fullstack orchestration
└── README.md                    # Platform documentation & setup guide
```

---

## 🌟 Core Interactive Arenas

| Module | Faculty Capabilities | Student Experience |
| :--- | :--- | :--- |
| **🎛️ Navigation Cockpit** | Centralized radial menu controlling stage states (Lobby, Quizzes, Flashcards, Typing, Q&A). | Instant synchronized state transition with zero manual refresh. |
| **🗳️ Live Polls & Surveys** | Broadcast dynamic MCQ questions, lock submissions, and reveal results with animated bar charts. | One-tap answer selection with instant visual feedback and score calculation. |
| **⌨️ Speed Typer Arena** | Launch typing challenges using code snippets with a live classroom racetrack. | Real-time keystroke tracking measuring WPM and accuracy against peers. |
| **📇 3D Flashcards** | 3D flip card animations with live audience confidence ratings (*Mastered*, *Reviewing*, *Confused*). | Interactive cards with flip transitions, rating controls, and notes broadcast. |
| **❓ Live Q&A Board** | Real-time question forum sorted by student upvotes (`votes DESC`) with instructor moderation. | Anonymous question posting and peer upvoting for priority topics. |
| **📈 Live Pace Meter** | Aggregate live comprehension gauge tracking student understanding in real time. | Discrete one-tap pace check (*"Understood"*, *"Getting Lost"*, *"Confused"*). |
| **🏆 Live Leaderboard** | Classroom standings summary with animated top 3 podium and streak multipliers. | Persistent personal standing banner displaying rank and score delta (+100 pts). |

---

## ⚡ Quick Start

### 1. Prerequisites
- **Node.js**: v18.0.0 or higher
- **npm** v9+ (Workspaces enabled)

### 2. Installation
```bash
# Clone the repository
git clone https://github.com/yashkoparde/engage.git
cd engage

# Install dependencies across all workspaces
npm install
```

### 3. Database Provisioning
Run the [`supabase_schema.sql`](apps/student/supabase_schema.sql) script in your Supabase SQL Editor to provision tables, indexes, and Realtime publications.

### 4. Running the Platform
```bash
# Run both Faculty and Student apps simultaneously
npm run dev

# Or run individual applications:
npm run dev:faculty   # Runs on http://localhost:5173
npm run dev:student   # Runs on http://localhost:5174

# Optional: Run backend socket server
npm run dev:server
```

---

## 📜 License
Distributed under the MIT License. See `LICENSE` for details.
