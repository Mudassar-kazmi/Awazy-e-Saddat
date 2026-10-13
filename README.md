# Awaz-e-Sadat — Professional Community Platform v6

Full-stack Node.js/Express/EJS community platform with a JSON file database for local/demo use.

## Included
- Admin login and protected admin moderation panel
- Member registration/login/profile search/follow
- Posts, reels, shorts, documentaries, interviews, news, majalis, announcements
- Long-form media uploads (application accepts up to 50GB per file; actual host/storage limits still apply)
- Stories with 24-hour expiry
- Camera capture and location field
- Books/documents: PDF, Word, Excel, PowerPoint, CSV, TXT, RTF, ODT/ODS/ODP, EPUB
- Creator edit/delete controls; admin can moderate/delete all content
- Individual and group chat
- Likes/comments
- AI assistant with Awaz-e-Sadat mission context and optional live web search through OpenAI
- Murree shrine/heritage gallery with source/credit fields

## Local run
1. Install Node.js 22 LTS or newer.
2. Open this folder in VS Code.
3. Run `npm install`.
4. Run `npm start`.
5. Open `http://localhost:3000`.

Admin credentials are stored in `.env`. **Do not upload `.env` to GitHub or any public repository.** Change the password before public deployment.

## AI
Set `OPENAI_API_KEY` in `.env`. Without a key the site remains in local/demo mode and will not perform live AI web research.

## Free publishing reality (important)
Render currently offers free Node/Express web services, but free services have an ephemeral filesystem: local uploaded files and local JSON/SQLite data can disappear on restart/redeploy/spindown. Render's free Postgres is also limited and expires after 30 days. See the official Render documentation before using it for real community data.

For a real public launch, move the database to persistent Postgres and move media to object storage. Supabase currently has a free plan with a 500MB database quota and 1GB storage, but its free file upload limit is 50MB, so it is **not suitable for 50GB videos on the free tier**.

### Recommended free demo
- Render Free Web Service for the Node/Express app.
- Keep large media local only for testing, or reduce upload limits for the free deployment.
- For production-scale documentaries/reels, use paid/object storage and a persistent database.

## Sources used for gallery research
- Mohra Sharif official portal: https://mohrasharif.com/
- Mohra Sharif official gallery: https://www.mohrasharif.com/index.php/gallery
- APP report on Surasi Syedan: https://www.app.com.pk/domestic/sufi-saints-role-in-preaching-islam-vital-gov-punjab/
- Wikimedia Commons GPO Chowk image: https://commons.wikimedia.org/wiki/File:GPO_Mall_Road_Murree,_Pakistan.jpg
- Flickr Mohra Sharif shrine interior: https://www.flickr.com/photos/murree/3203761906


## v7 fixes and important setup notes

- Public Books list: anyone can read/download published documents; logged-in members can like them.
- Groups are public/discoverable. Members can search people, search groups, open a group and join by opening it. Admin overview includes groups and recent direct/group messages for moderation.
- Welfare requests are shown in the confidential admin inbox; a case ID is returned to the person submitting the form.
- The homepage introduces the mission; `/intro` is the dedicated mission/how-it-works page.
- Footer contact: mudassarkazmi112233@gmail.com, +92 314 5245180, awazy-e-sadatcare@gmail.com, developed by Syed Mudassar Ali Kazmi.
- Add the real Facebook/YouTube/Instagram/TikTok/WhatsApp profile URLs to `.env` before publishing; the project does not invent social account links.
- AI answers the platform mission offline. General live AI answers and automatic web search require a valid API key. Without it, the AI provides a direct Google search link rather than pretending it searched. API use may incur charges.
- Gallery falls back to a locally bundled archive illustration if an external image host blocks the image. This is not a substitute for the actual shrine photograph; local shrine entries without verified images still need original/licensed photos.

## Admin monitoring and privacy

Sign in at `/admin` using the credentials stored in your private `.env`. The admin inbox includes welfare requests, public groups, recent chat messages and published books. Welfare request details are sensitive and should only be accessed by authorized admins. Before public hosting, change the admin password and configure environment variables in the hosting provider; never commit `.env`.


## Google Search indexing

The app provides `/robots.txt` and `/sitemap.xml`. After you own/configure the domain, set `SITE_URL=https://your-domain` in the hosting environment, then add the verified domain in Google Search Console and submit `https://your-domain/sitemap.xml`. Google indexing is free but not instant or guaranteed. Owning a domain such as `awazy-e-sadat.org` normally requires registering/paying for that domain; a free host subdomain can be used first.


## Local admin login

Open `/admin`. If you have not created a `.env` file, the local defaults are `admin@awazesadat.local` and `change-me-now`. If using `.env.example`, copy it to `.env` and set a private password. Never deploy the sample password: on Render, set a strong unique `ADMIN_PASSWORD` and your chosen `ADMIN_EMAIL` in the service Environment settings.
