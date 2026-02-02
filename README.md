# Pinterest Clone

A full-stack Pinterest clone built with Next.js, React, and Neon PostgreSQL.

## Features

- **User Authentication** - Sign up, login, and logout with secure JWT tokens
- **Pin Discovery** - Browse and search pins on the discover page
- **Create Pins** - Upload and share pins with title, description, and image URL
- **Boards** - Organize pins into custom collections
- **Social Features**:
  - Like and unlike pins
  - Add comments to pins
  - Follow and unfollow users
  - View user profiles
- **Search** - Search pins by title and description
- **Infinite Scroll** - Auto-load more pins as you scroll

## Tech Stack

- **Frontend**: Next.js 16, React 19, TypeScript, Tailwind CSS, shadcn/ui
- **Backend**: Next.js API Routes, Node.js
- **Database**: Neon PostgreSQL with custom query utilities
- **Authentication**: JWT with HTTP-only cookies
- **Password Security**: bcryptjs for password hashing

## Setup Instructions

### 1. Environment Variables

Copy `.env.example` to `.env.local` and fill in your values:

```bash
cp .env.example .env.local
```

Key environment variables needed:
- `DATABASE_URL` - Your Neon PostgreSQL connection string
- `JWT_SECRET` - A secure random string for JWT signing (change in production)

### 2. Install Dependencies

```bash
npm install
```

Key dependencies:
- `@neondatabase/serverless` - Neon PostgreSQL client
- `bcryptjs` - Password hashing
- `next` - React framework
- `tailwindcss` - CSS framework

### 3. Run the Application

```bash
npm run dev
```

Visit `http://localhost:3000` to see your Pinterest clone!

## API Routes

### Authentication
- `POST /api/auth/signup` - Create new user account
- `POST /api/auth/login` - Login user
- `POST /api/auth/logout` - Logout user
- `GET /api/auth/me` - Get current user info

### Pins
- `GET /api/pins` - Get all pins (paginated)
- `POST /api/pins` - Create new pin (requires auth)
- `GET /api/pins/[id]` - Get pin details
- `POST /api/pins/[id]/like` - Toggle like on pin
- `GET /api/pins/[id]/comments` - Get pin comments
- `POST /api/pins/[id]/comments` - Add comment to pin

### Boards
- `POST /api/boards` - Create new board (requires auth)

### Search
- `GET /api/search` - Search pins by query

### Users
- `GET /api/users/[id]` - Get user profile and pins
- `POST /api/users/[id]/follow` - Toggle follow user

## Database Schema

The app uses these main tables:
- `users` - User accounts and profiles
- `pins` - Pins with title, description, and image
- `boards` - Collections for organizing pins
- `likes` - Track pin likes
- `comments` - Comments on pins
- `followers` - User follow relationships

## Key Components

- **AuthProvider** - Global auth state management
- **Navbar** - Navigation with search
- **PinCard** - Reusable pin display component
- **LoginForm / SignupForm** - Auth forms
- **Pages**:
  - `/` - Discover page with all pins
  - `/auth` - Login/signup
  - `/create` - Create new pin
  - `/search` - Search results
  - `/profile/[username]` - User profile
  - `/pins/[id]` - Pin details with comments

## Notes

- All passwords are hashed with bcryptjs (10 salt rounds)
- JWT tokens are stored in HTTP-only cookies for security
- Images are loaded from external URLs (you can use any image hosting service)
- The database connection uses Neon's serverless client for optimal performance

## Future Enhancements

- User profile image uploads
- Image optimization and caching
- Collaborative boards
- Pin editing and deletion
- User notifications
- Advanced search filters
- Dark mode support
