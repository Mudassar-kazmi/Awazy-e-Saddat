# Awaz-e-Sadat — durable storage and Render deployment

## Important storage facts

This application currently stores structured records (users, posts, books, comments, etc.) in `data/db.json` and uploaded files in the uploads directory. On the same computer, these should survive `npm start` stopping and starting again as long as you run the same project folder and do not delete those files. If they disappear locally, check that the terminal is running the same folder and inspect `data/db.json` and `public/uploads`.

A normal Render free web service has an ephemeral filesystem. Do not use it for real community data: files and the JSON database can be lost on restart, redeploy, or instance replacement.

## Render configuration for durable initial deployment

This ZIP supports configurable data/upload paths. For persistence on Render, create a **paid persistent disk** attached to the web service and mount it at `/var/data`. Then add these environment variables in the Render service settings:

- `DATA_DIR=/var/data`
- `UPLOADS_DIR=/var/data/uploads`
- `NODE_ENV=production`
- `ADMIN_EMAIL=your-real-admin-email`
- `ADMIN_PASSWORD=` set a strong unique password
- `SITE_URL=https://your-live-site.onrender.com` (use your actual URL)

Set the Render Health Check Path to `/api/health`. Use Build Command `npm install` and Start Command `npm start`. The first start on an empty persistent disk copies the included starter `data/db.json` into the mounted data directory. After deploying, test uploading a small PDF, open it, restart/redeploy the service, and verify the same book still opens. Do not upload important user data until this test passes.

## Limits and scale warning

A persistent disk protects files from ordinary service restarts/redeploys, but it is not a backup, does not provide automatic disaster recovery by itself, and this app's JSON database is not a suitable final database for millions of active users. For a serious public launch, migrate records to managed PostgreSQL, uploads to durable object storage (such as an S3-compatible service), configure automated backups/retention, monitoring, malware scanning, rate limiting, and test recovery. Large videos should use object storage plus a CDN, not the web server's local disk.

## Keep secrets private

The ZIP intentionally does not include your `.env` file. Never upload API keys or passwords to GitHub or share them in chat. Configure secrets through the hosting provider's environment settings.

## Local test

1. Extract the ZIP into a new folder (keep your existing folder as a backup).
2. Open that folder in VS Code.
3. Run `npm install`, then `npm start`.
4. Upload a small test book. Stop the server with Ctrl+C, then run `npm start` again.
5. If testing locally, confirm the record is still present in `data/db.json` and its file remains under `public/uploads`.
