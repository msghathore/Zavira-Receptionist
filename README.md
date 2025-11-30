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

Create a Supabase project and table:

```sql
CREATE TABLE appointments (
  id SERIAL PRIMARY KEY,
  name TEXT NOT NULL,
  date DATE NOT NULL,
  time TIME NOT NULL,
  purpose TEXT
);
```

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