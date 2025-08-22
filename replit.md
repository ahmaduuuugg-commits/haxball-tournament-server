# RHL Tournament - Haxball Headless Server

## Overview

This is a Node.js server application designed to host and manage Haxball tournament rooms using Puppeteer for browser automation. The system creates and maintains persistent Haxball game rooms with advanced tournament features including Discord integration, player management, and real-time monitoring capabilities.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Web Server Architecture
- **Framework**: Express.js for HTTP server and API endpoints
- **Static Content**: Serves a dashboard interface from the `public/` directory
- **Health Monitoring**: Built-in health check endpoints (`/health`, `/status`) for system monitoring
- **Manual Controls**: REST API endpoint for manual server restart (`/restart`)

### Browser Automation Layer
- **Engine**: Puppeteer for headless Chrome browser control
- **Purpose**: Automates Haxball room creation and management through browser interaction
- **Persistence**: Maintains browser instances with global state tracking for room status

### Configuration Management
- **Environment Variables**: Uses dotenv for configuration management
- **Centralized Config**: `utils/config.js` centralizes all application settings
- **Geographic Settings**: Configurable server location for optimal ping (defaulting to Egypt)

### Logging System
- **Library**: Winston for structured logging
- **File Rotation**: Automatic log rotation with size limits (5MB, 5 files)
- **Log Levels**: Separate error and combined logs with console output in development

### Frontend Dashboard
- **Technology**: Vanilla HTML/CSS/JavaScript
- **Purpose**: Real-time status monitoring interface
- **Features**: Server status, room status, player count, and uptime display
- **Styling**: CSS Grid layout with responsive design and Font Awesome icons

### Game Room Management
- **Haxball Integration**: Direct integration with Haxball's headless API
- **Tournament Features**: Admin management, club systems, player statistics
- **State Persistence**: Maintains game state across sessions with permanent admin saving

### Keep-Alive System
- **Purpose**: Prevents server hibernation on hosting platforms
- **Implementation**: HTTP ping system with configurable intervals
- **Default**: 5-minute ping intervals to maintain server activity

## External Dependencies

### Core Dependencies
- **Express**: Web server framework for REST API and static file serving
- **Puppeteer**: Headless browser automation for Haxball room management
- **Winston**: Logging library for structured application logging
- **dotenv**: Environment variable management
- **node-cron**: Task scheduling for automated operations
- **ws**: WebSocket support for real-time communication

### HTTP Client Libraries
- **axios**: Primary HTTP client for API requests
- **node-fetch**: Alternative fetch implementation for HTTP operations

### Discord Integration
- **Discord Webhooks**: Real-time notifications and tournament updates
- **Configuration**: Webhook URLs, channel IDs, and role mentions for community integration

### Haxball Platform
- **Headless API**: Direct integration with Haxball's browser-based game engine
- **Token Authentication**: Requires valid Haxball API token for room creation
- **Geographic Optimization**: Server location configuration for regional player optimization

### Hosting Platform Dependencies
- **Port Configuration**: Dynamic port assignment for cloud hosting compatibility
- **Process Management**: Built-in restart mechanisms and health monitoring
- **Memory Monitoring**: Process memory usage tracking and reporting