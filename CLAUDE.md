# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

LifeStint is a productivity app for tracking focused work sessions ("stints") across multiple projects. It provides a dashboard-based interface where users can start/stop/pause work sessions, track progress towards daily goals, and analyze their productivity patterns.

**Key Concepts:**
- **Stints**: Timed work sessions with configurable durations (default 2 hours)
- **Projects**: Containers for work with daily stint goals and customizable settings
- **Active Session**: Only one stint can be active at a time across all projects
- **Progress Tracking**: Daily stint progress badges (e.g., "2 of 3 stints today")

## Tech Stack

- **Framework**: Next.js 15.4.6 with App Router
- **Language**: TypeScript with strict mode
- **Styling**: Tailwind CSS v4
- **Backend**: Supabase (planned)
- **Authentication**: Supabase Auth (planned)
- **Fonts**: Geist Sans and Geist Mono from Google Fonts

## Development Commands

```bash
# Start development server
npm run dev

# Build for production
npm run build

# Start production server
npm start

# Run linter
npm run lint
```

## Project Structure

```
src/
├── app/                    # Next.js App Router
│   ├── layout.tsx         # Root layout with font configuration
│   ├── page.tsx           # Homepage (currently default Next.js template)
│   └── globals.css        # Global Tailwind styles
├── docs/
│   └── PRD.md             # Product Requirements Document
```

## Architecture Guidelines

### State Management
- **Timer State**: Active stint tracking with real-time updates
- **Project State**: Multiple projects with individual configurations
- **Session State**: Pause/resume functionality with time tracking
- **Progress State**: Daily stint counters per project

### Key Features to Implement
- **Dashboard**: Project cards with stint progress and timer display
- **Session Management**: Start/pause/stop with automatic session switching
- **Project Management**: CRUD operations with modal dialogs
- **Notifications**: Browser notifications for stint completion
- **Data Persistence**: Supabase integration for all app data
- **Markdown Support**: Notes/comments with markdown rendering

### UI/UX Patterns
- **Single Active Session**: Visual highlighting of active stint with prominent timer
- **Progress Indicators**: Badge-style progress display (e.g., "1 of 3 stints today")
- **Modal Workflows**: Project creation and editing in overlay dialogs
- **Responsive Design**: Desktop and mobile browser compatibility

### Path Aliases
- `@/*` maps to `./src/*` for clean imports

## Development Workflow

1. **Feature Development**: Focus on dashboard-first approach with project cards
2. **Timer Implementation**: Real-time updates without page reloads
3. **Data Layer**: Plan for Supabase integration from the start
4. **Testing**: Ensure timer accuracy and session state management
5. **Notifications**: Implement browser notification permissions and delivery

## Performance Requirements

- Instant UI updates for timer and session state
- Handle hundreds of projects and thousands of stints
- Real-time timer updates without performance degradation
- Cross-browser compatibility for notifications API