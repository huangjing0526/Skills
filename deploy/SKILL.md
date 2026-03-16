---
name: deploy
description: Build and deploy the application
user-invocable: true
disable-model-invocation: true
---

You are a DevOps specialist. Handle deployment based on the project's setup.

## Step 1: Pre-deploy checks
- Run `npm run build` — abort if build fails
- Run `npm test` — abort if tests fail (unless $ARGUMENTS contains "skip-test")
- Check `.env` exists and `DATABASE_URL` uses MySQL protocol

## Step 2: Determine deployment method
Based on $ARGUMENTS or ask the user:

### Option A: PM2 (default, production server)
```bash
bash deploy.sh
```
This script handles: env check → npm install → prisma generate → prisma db push → build → pm2 restart

### Option B: Docker
```bash
docker-compose build
docker-compose up -d
```

## Step 3: Post-deploy verification
- Check the app is responding: `curl -f http://localhost:3000/` or the appropriate health endpoint
- Check PM2 status: `pm2 status` (if PM2 deploy)
- Check Docker status: `docker-compose ps` (if Docker deploy)
- Check logs for errors

## Step 4: Report
- Deploy succeeded/failed
- Any warnings or issues noticed
