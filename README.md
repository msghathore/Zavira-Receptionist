# Zavira Receptionist

A LiveKit voice AI receptionist agent built with Node.js and TypeScript.

## Features

- Voice-based receptionist interactions
- Appointment scheduling and checking
- Integration with Supabase for data storage
- Deployable on Vercel or as Docker container

## Setup

1. Clone the repository
2. Install dependencies: `pnpm install`
3. Download ML models: `pnpm run download-files`
4. Copy `.env.example` to `.env` and fill in your API keys
5. Build: `pnpm run build`
6. Run: `pnpm run start`

## Environment Variables

See `.env.example` for required variables. You need:

- LiveKit credentials
- OpenAI API key
- AssemblyAI API key
- Cartesia API key
- Supabase URL and anon key

## Database Setup

Create a Supabase project and ensure the `appointments` table exists with the following schema:

```sql
-- The appointments table should have these columns:
-- id (UUID, primary key)
-- full_name (TEXT)
-- appointment_date (DATE)
-- appointment_time (TIME)
-- notes (TEXT)
-- Other columns as needed for your application
```

The agent will use the `full_name`, `appointment_date`, `appointment_time`, and `notes` columns for appointment management.

## Deployment

### Docker

Build and run the Docker container:

```bash
docker build -t zavira-receptionist .
docker run -e LIVEKIT_URL=$LIVEKIT_URL -e LIVEKIT_API_KEY=$LIVEKIT_API_KEY -e LIVEKIT_API_SECRET=$LIVEKIT_API_SECRET zavira-receptionist
```

### Vercel

Deploy as a serverless function. Ensure environment variables are set in Vercel dashboard.

## Development

- `pnpm run dev` for development with hot reload
- `pnpm run typecheck` for TypeScript checking
- `pnpm run lint` for linting