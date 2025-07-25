# SHHC Betting Platform

## Overview

This is a hockey betting platform called SHHC (Sports Hockey Betting Platform) built with a modern full-stack architecture. The application allows users to place traditional bets on hockey games and submit goal predictions for individual players that require staff approval. Users start with $500 in fake money and can view leaderboards and manage their betting activities in real-time.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **UI Framework**: shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with custom SHHC theme variables
- **State Management**: TanStack Query (React Query) for server state
- **Routing**: Wouter for lightweight client-side routing
- **Forms**: React Hook Form with Zod validation

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **Database ORM**: Drizzle ORM with PostgreSQL dialect
- **Database Provider**: Neon Database (serverless PostgreSQL)
- **Session Management**: Express sessions with PostgreSQL store
- **API Design**: RESTful endpoints with JSON responses

### Database Design
The application uses PostgreSQL with three main tables:
- **Users**: Stores user profiles, balances, and betting statistics
- **Games**: Hockey game information including teams, odds, and results
- **Bets**: Individual bet records linking users to games

## Key Components

### Core Features
1. **User Management**: Basic user creation and balance tracking (starts with $500)
2. **Traditional Game Betting**: Place bets on hockey games with different bet types (home/away/draw)
3. **Goal Predictions**: Submit predictions for specific players' goal counts that require staff approval
4. **Staff Approval System**: Staff members can approve or reject goal predictions
5. **Real-time Updates**: Live game status and betting slip management
6. **Leaderboard**: User rankings based on winnings and performance
7. **Balance Management**: Track user funds and betting history

### UI Components
- **Dashboard**: Main interface showing games, betting slip, and leaderboard
- **Game Cards**: Interactive cards for each hockey game with betting options
- **Betting Slip**: Shopping cart-style interface for managing selected bets
- **Sidebar Navigation**: User balance and navigation menu
- **Responsive Design**: Mobile-friendly layout with dark theme

### Data Storage Strategy
- **In-Memory Storage**: Currently uses MemStorage class for development
- **Production Ready**: Configured for PostgreSQL with Drizzle ORM
- **Sample Data**: Pre-populated with hockey teams and demo users

## Data Flow

1. **User Authentication**: Simple username-based system (currently "You" as default user)
2. **Game Loading**: Fetch available hockey games from `/api/games`
3. **Bet Placement**: Add bets to client-side betting slip, validate, then submit to `/api/bets`
4. **Balance Updates**: Real-time balance updates after successful bet placement
5. **Leaderboard**: Fetch and display user rankings from `/api/leaderboard`

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: Serverless PostgreSQL driver
- **drizzle-orm**: Type-safe database ORM
- **@tanstack/react-query**: Server state management
- **wouter**: Lightweight React router
- **@radix-ui/***: Accessible UI primitives
- **tailwindcss**: Utility-first CSS framework
- **zod**: Schema validation library

### Development Tools
- **Vite**: Build tool with HMR
- **TypeScript**: Type safety
- **ESBuild**: Production bundling
- **Replit Integration**: Development environment support

## Deployment Strategy

### Development
- **Local Development**: `npm run dev` starts both frontend and backend
- **Hot Reload**: Vite provides instant updates for frontend changes
- **Database**: Uses Drizzle Kit for schema management with `npm run db:push`

### Production Build
- **Frontend**: Vite builds optimized React bundle to `dist/public`
- **Backend**: ESBuild bundles server code to `dist/index.js`
- **Database Migrations**: Drizzle generates migrations in `./migrations`
- **Environment**: Requires `DATABASE_URL` environment variable

### Deployment Targets
- **Replit**: Native support with cartographer plugin for development
- **Serverless**: Compatible with Vercel, Netlify, or similar platforms
- **Traditional Hosting**: Can run on any Node.js hosting environment

### Configuration Notes
- The application expects PostgreSQL as the production database
- Session storage uses `connect-pg-simple` for PostgreSQL session store
- CORS and security headers should be configured for production
- Environment variables needed: `DATABASE_URL`, `NODE_ENV`