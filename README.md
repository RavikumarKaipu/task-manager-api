# Task Manager API

A small Express + MongoDB API intended for AWS EC2 deployment practice.

## Requirements
- Node.js 20 or newer
- MongoDB Atlas M0 cluster (or another MongoDB instance)

## Run locally
1. Copy `.env.example` to `.env`.
2. Put your MongoDB connection string in `MONGO_URI`.
3. Install dependencies: `npm install`
4. Start: `npm run dev`
5. Open `http://localhost:5000/health`

## API endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/` | API welcome |
| GET | `/health` | Health check |
| GET | `/api/tasks` | List tasks |
| POST | `/api/tasks` | Create task |
| GET | `/api/tasks/:id` | Get one task |
| PUT | `/api/tasks/:id` | Update task |
| DELETE | `/api/tasks/:id` | Delete task |

### Create task example
POST `/api/tasks`
```json
{
  "title": "Deploy backend to AWS",
  "description": "Practice EC2, Nginx and HTTPS",
  "completed": false
}
```

## Deployment notes
- Keep `.env` out of Git; `.gitignore` already excludes it.
- Configure MongoDB Atlas Network Access to allow the EC2 instance's outbound public IP.
- Do not expose port 5000 publicly in the final setup. Nginx will proxy HTTPS traffic to the app.
