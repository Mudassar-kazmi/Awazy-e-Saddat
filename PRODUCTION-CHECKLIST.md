# Production checklist

- [x] Unified social feed
- [x] Profile archive for approved user content
- [x] Search member profiles
- [x] Follow / unfollow
- [x] Likes and comments
- [x] User can delete own content only
- [x] Server-enforced admin moderation
- [x] Admin suspend / block / activate
- [x] Admin can delete any content
- [x] Reels / shorts / documentary / long-video categories
- [x] 50 GB configured single-file limit (hosting limits still apply)
- [x] AI endpoint with web-search tool when API key is configured
- [x] Public group directory and admin group/message monitoring
- [x] Public book downloads and likes for logged-in members
- [x] Admin welfare request inbox and status workflow
- [x] Mission/intro page, contact footer, robots.txt and sitemap.xml

## Before public launch
- [ ] Move data to managed PostgreSQL (JSON file is for demo/early testing only)
- [ ] Persistent session store
- [ ] HTTPS
- [ ] CSRF and rate limiting
- [ ] Malware/virus scanning
- [ ] Object storage + CDN for long videos and all user uploads
- [ ] Backups and monitoring
- [ ] Privacy policy, terms, consent and copyright/takedown workflow
- [ ] Real email/push/WhatsApp notification providers
- [ ] Configure social account URLs/API integrations
- [ ] Change development admin credentials
