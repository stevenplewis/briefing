# briefing

A finite daily digest for Reddit. No infinite scroll, no algorithm — just the best posts from your subreddits, then you're done.

## How it works

- Fetches top posts from your subscribed subreddits via Reddit's public JSON feeds
- **Normalizes scores** across subs so a breakout post in a small community ranks alongside big-sub hits
- Caps at **2 posts per subreddit** for diversity
- Posts auto-mark as **read** when you scroll past them
- Progress bar tracks your reading — once you're done, it tells you to go enjoy your day

## Setup

### Quick start (local)

Serve the file locally:

```bash
npx serve .
# or
python3 -m http.server 3000
```

Open `http://localhost:3000` in your browser.

### Deploy to GitHub Pages

1. Fork or clone this repo
2. Go to **Settings → Pages**
3. Set source to **main** branch, root folder
4. Your digest will be live at `https://yourusername.github.io/briefing/`
5. On mobile, open the URL and **Add to Home Screen** for an app-like experience

### Customize your subreddits

Either edit the `DEFAULT_SUBS` array in `index.html`, or use the settings panel (☰ icon) to add/remove subs in the UI. Changes persist in your browser's localStorage.

## Configuration

All configurable via the settings panel:

| Setting | Options | Default |
|---------|---------|---------|
| Sort by | Top / Discussed / Newest | Top |
| Time range | Hot / Today / This week | Today |

## Architecture

Single HTML file. No build step, no dependencies, no backend. Uses:

- Reddit's public `.json` endpoints for data
- [corsproxy.io](https://corsproxy.io) to bypass CORS (see comments in code for self-hosting alternatives)
- `localStorage` for preferences and read state
- `IntersectionObserver` for scroll-based read tracking

## Future ideas

- [ ] Cloudflare Worker to replace CORS proxy
- [ ] Server-side caching (fetch once per morning)
- [ ] PWA manifest for proper mobile install
- [ ] Per-sub priority weighting

## License

MIT
