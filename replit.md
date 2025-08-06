# Trading Platform Application

## Overview

This is a full-stack trading platform application built with modern web technologies. The application provides real-time trading functionality with features including market data visualization, order management, portfolio tracking, and WebSocket-based real-time updates. It follows a monorepo structure with a React frontend, Express.js backend, and PostgreSQL database using Drizzle ORM.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Styling**: Tailwind CSS with custom trading-specific color scheme
- **UI Components**: shadcn/ui component library built on Radix UI primitives
- **State Management**: TanStack Query (React Query) for server state management
- **Routing**: Wouter for lightweight client-side routing
- **Charts**: Lightweight Charts library for financial data visualization
- **Build Tool**: Vite for fast development and optimized builds

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **WebSocket**: Native WebSocket server for real-time data streams
- **Session Management**: Express sessions with PostgreSQL storage
- **Development**: tsx for TypeScript execution in development

### Database Architecture
- **Database**: PostgreSQL
- **ORM**: Drizzle ORM with Drizzle Kit for migrations
- **Connection**: Neon Database serverless PostgreSQL
- **Schema**: Shared schema definitions between frontend and backend

## Key Components

### Database Schema (shared/schema.ts)
- **Users**: Authentication and user management
- **Symbols**: Trading instruments (crypto, stocks, forex)
- **Watchlists**: User-customizable symbol tracking
- **Orders**: Trading order management with different types (market, limit, stop)
- **Positions**: Current holdings and P&L tracking
- **Candles**: OHLCV price data for charts
- **Market Depth**: Order book data
- **Trades**: Historical trade records
- **News**: Market news and updates

### Frontend Components
- **Trading Interface**: Main trading dashboard with chart, order book, and controls
- **Chart System**: Advanced financial charting with multiple timeframes and indicators
- **WebSocket Integration**: Real-time price updates and market data
- **Order Management**: Modal-based order entry with validation
- **Watchlist**: Sidebar for tracking favorite symbols
- **Market Depth**: Order book visualization

### Backend Services
- **Storage Layer**: In-memory storage implementation with interface for future database integration
- **WebSocket Server**: Real-time data broadcasting to connected clients
- **API Routes**: RESTful endpoints for CRUD operations
- **Price Simulation**: Mock real-time price generation for development

## Data Flow

1. **Client Connection**: Frontend establishes WebSocket connection on page load
2. **Initial Data**: Server sends current symbols, prices, and market data
3. **Real-time Updates**: Server broadcasts price changes, new trades, and market depth updates
4. **User Actions**: Orders submitted via REST API, real-time updates via WebSocket
5. **State Synchronization**: React Query manages server state with real-time WebSocket updates

## External Dependencies

### Core Dependencies
- **Database**: Neon PostgreSQL serverless database
- **UI Framework**: Radix UI primitives for accessible components
- **Charting**: TradingView's Lightweight Charts library
- **Validation**: Zod for schema validation
- **Styling**: Tailwind CSS with PostCSS

### Development Tools
- **TypeScript**: Full type safety across the stack
- **Vite**: Fast development server and build tool
- **ESBuild**: Fast TypeScript compilation for production
- **Drizzle Kit**: Database schema management and migrations

## Deployment Strategy

### Development
- **Frontend**: Vite dev server with HMR
- **Backend**: tsx for TypeScript execution
- **Database**: Drizzle Kit for schema changes
- **Environment**: Development-specific configurations

### Production Build
- **Frontend**: Vite build to static assets
- **Backend**: ESBuild compilation to single JavaScript file
- **Deployment**: Single Node.js process serving both API and static files
- **Database**: Production PostgreSQL with connection pooling

### Key Architectural Decisions

1. **Monorepo Structure**: Shared TypeScript types and schemas between frontend and backend for type safety
2. **WebSocket for Real-time**: Chosen over Server-Sent Events for bidirectional communication needs
3. **In-memory Storage**: Current implementation for rapid development, designed for easy database migration
4. **Component-based UI**: shadcn/ui for consistent, accessible interface components
5. **Query-based State**: TanStack Query for efficient server state management with caching
6. **TypeScript Throughout**: Full type safety from database schema to UI components

The application is designed for scalability with clear separation of concerns, making it easy to migrate from in-memory storage to a full database implementation and add additional trading features.