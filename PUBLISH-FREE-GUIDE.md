# Publish Awaz-e-Sadat for free — beginner guide

## First: test on your PC
1. Extract `Awaz-e-Sadat-FULL-PROFESSIONAL-v7-FIXED.zip` to a simple folder, for example `C:\awaz-e-sadat`.
2. Open that folder in VS Code.
3. Open Terminal → New Terminal.
4. Run `npm install` and wait for it to finish.
5. Run `npm start`.
6. Open `http://localhost:3000`.
7. Test registration, member search, public groups, books, welfare request, AI mission answer and `/admin`.

## Recommended free hosting choices

### Option A — Oracle Cloud Always Free VM (best fit for this Express app if your account/region has capacity)
- Oracle documents Always Free compute resources, but capacity may be unavailable in a region and signup usually requires identity/payment-card verification.
- A VM can run Node.js/Express and keep app files on its disk, but you must configure Linux, firewall ports, HTTPS, backups, and a process manager yourself.
- Do not assume a VM or its storage is automatically backed up. Make regular copies of `data/db.json` and `public/uploads`.
- Official docs: https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm

### Option B — Render free web service (quick demo only)
- Render supports free Node.js web services, but the free service can sleep after inactivity and its filesystem is ephemeral. Uploaded files and `data/db.json` can disappear after restart/redeploy/spin-down.
- Use it for a temporary demo only until persistent database and file storage are configured.
- Official docs: https://render.com/docs/free

### Option C — Netlify
- Netlify can run Express through serverless functions, but this app currently expects a persistent Node server and local writable storage. Netlify's function request payload limits are far too small for large video uploads, so do not use it for the current 50GB-upload goal without a major architecture change and external storage.
- Official docs: https://docs.netlify.com/build/frameworks/framework-setup-guides/express/ and https://docs.netlify.com/build/functions/configuration/

## Before putting real community data online
- This version still uses a local JSON database. For a real public community site, migrate users, posts, groups, messages and welfare records to a persistent database (PostgreSQL/MySQL) and media to persistent object storage.
- Set the admin password to a new strong password before launch.
- Set `ADMIN_EMAIL`, `ADMIN_PASSWORD`, `OPENAI_API_KEY`, `OPENAI_MODEL`, `SITE_URL`, and actual social profile URLs as hosting environment variables. Do not upload `.env` to a public repository.
- A valid AI API key may cost money. Without it, the AI can explain the platform mission offline and offers a Google search link for other questions.
- The configured 50GB file limit is only an application setting, not a promise that free hosting can accept or store files that large. Keep long videos on a storage/video service designed for them.

## Domain and Google Search
- You can start with the free subdomain provided by your host.
- A custom domain such as `awazy-e-sadat.org` normally requires domain registration and a renewal fee; hosting may be free while the domain itself is not.
- After your domain points to the live website and HTTPS works, set `SITE_URL=https://your-domain` in the host environment.
- Open Google Search Console, verify domain ownership, and submit `https://your-domain/sitemap.xml`. The project generates `robots.txt` and `sitemap.xml`; Google indexing is free but may take time and is not guaranteed.

## Final verification checklist
- Test in a private/incognito browser after deployment.
- Register a normal member and upload a small test document/image.
- Create a public group, post a message, then sign in as admin and confirm the group/message appear in the admin inbox.
- Submit a test welfare request and verify the case appears in the admin inbox; then delete the test record if needed.
- Confirm the social links point to your real official accounts.
- Never use real sensitive welfare details until secure hosting, backups, access controls and privacy terms are in place.
