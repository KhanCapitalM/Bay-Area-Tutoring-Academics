# Bay Area Tutoring Academy Website Project

## Overview

This project is a full-stack web application for the Bay Area Tutoring Academy. It features a modern React frontend with an Express backend and uses Drizzle ORM for database operations. The application has a clean architecture with client-side and server-side code separated, making it easy to maintain and extend.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

The application follows a modern fullstack JavaScript architecture:

1. **Frontend**: React-based SPA (Single Page Application) using shadcn/UI components and TailwindCSS for styling
2. **Backend**: Express.js API server 
3. **Database**: PostgreSQL with Drizzle ORM for type-safe database interactions
4. **Development Environment**: Vite for frontend development with HMR (Hot Module Replacement)
5. **API Communication**: RESTful API endpoints prefixed with `/api`

The application is structured in a monorepo pattern with separate directories for client, server, and shared code. The shared directory contains schema definitions used by both the frontend and backend.

## Key Components

### Frontend Components

1. **Page Components**: 
   - Home.tsx: Main landing page with various sections
   - NotFound.tsx: 404 error page

2. **UI Components**:
   - Header: Navigation and branding
   - Hero: Main banner section
   - Features: Highlights of tutoring services
   - Programs: Different tutoring programs offered
   - Testimonials: Client feedback displayed in a carousel
   - ContactSection: Contact information and form
   - Footer: Site navigation and legal information

3. **UI Library**: 
   - The project uses shadcn/UI, a collection of reusable components built with Radix UI and styled with Tailwind CSS
   - Components are located in `client/src/components/ui`

4. **State Management**:
   - React Query for data fetching and state management
   - Custom hooks for UI state (e.g., mobile detection)

### Backend Components

1. **Express Server**:
   - Main entry point in server/index.ts
   - API routes defined in server/routes.ts

2. **Storage Interface**:
   - Abstract interface for database operations in server/storage.ts
   - Currently using an in-memory implementation (MemStorage)
   - Designed to be replaced with a database implementation

3. **Database Schema**:
   - Defined in shared/schema.ts using Drizzle ORM
   - Currently includes a users table with basic authentication fields

## Data Flow

1. **Client-to-Server Communication**:
   - Frontend components make HTTP requests to the API endpoints
   - React Query used for managing API requests and response data
   - All API routes are prefixed with `/api`

2. **Database Operations**:
   - Server uses the storage interface to interact with the database
   - Drizzle ORM provides type-safe database access
   - Schema validation with Zod ensures data integrity

3. **Authentication Flow**:
   - Basic user authentication schema is defined but not fully implemented
   - User registration and login functionality to be built using the existing schema

## External Dependencies

### Frontend Dependencies
- React for UI components
- Tailwind CSS for styling
- shadcn/UI component library based on Radix UI
- TanStack React Query for data fetching and state management
- wouter for client-side routing
- Lucide for icons
- react-day-picker for date selection
- Embla Carousel for carousel/slider functionality

### Backend Dependencies
- Express.js for the web server
- Drizzle ORM for database operations
- Zod for schema validation
- Connect-pg-simple (prepared for session management)
- @neondatabase/serverless for potential serverless PostgreSQL connection

## Deployment Strategy

The application is configured for deployment on Replit with:

1. **Build Process**:
   - `npm run build` command builds both client and server
   - Vite builds the client-side code
   - esbuild bundles the server code

2. **Runtime Environment**:
   - Node.js 20 for server execution
   - PostgreSQL database (version 16)
   - Environment variables control configuration settings

3. **Deployment Configuration**:
   - The .replit file defines deployment settings
   - Port mapping: local port 5000 mapped to external port 80
   - Autoscaling deployment target for better performance

The application requires a PostgreSQL database to be provisioned with the proper connection string set in the DATABASE_URL environment variable.

## Development Workflow

1. **Local Development**:
   - Run `npm run dev` to start both client and server in development mode
   - Client uses Vite's hot module replacement for fast updates
   - Backend auto-reloads with tsx

2. **Database Management**:
   - Use `npm run db:push` to push schema changes to the database
   - Schema is defined in shared/schema.ts

3. **Building for Production**:
   - Run `npm run build` to create production bundles
   - Run `npm run start` to start the production server

4. **Code Organization**:
   - Shared code in `/shared` directory
   - Frontend code in `/client` directory
   - Backend code in `/server` directory