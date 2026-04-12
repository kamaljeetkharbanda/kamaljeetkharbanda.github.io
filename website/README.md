# AIMLEngineers.com Website

## Folder Structure

```
website/
├── index.html              ← Main landing page
├── team.html               ← Team page (loads from data/team.json)
├── data/
│   └── team.json           ← ✏️ EDIT THIS FILE to add/remove team members
└── images/
    └── team/               ← Drop team member photos here
        ├── jane-smith.jpg
        ├── john-doe.jpg
        └── ...
```

## How to Add a Team Member

**1. Add their photo** to `images/team/` (use lowercase, hyphens: `first-last.jpg`)
   - Recommended: square crop, at least 300x300px
   - Supported: .jpg, .png, .webp

**2. Open `data/team.json`** and add a new entry:

```json
{
    "name": "Jane Smith",
    "role": "Instructor — LangChain & Agents",
    "department": "Instructors",
    "bio": "Deep expertise in LangChain, LangGraph, and multi-agent systems.",
    "photo": "images/team/jane-smith.jpg",
    "linkedin": "https://linkedin.com/in/janesmith",
    "color": "purple"
}
```

**3. Push to GitHub.** Done. No HTML editing needed.

### Field Reference

| Field | Required | Description |
|-------|----------|-------------|
| `name` | Yes | Full name |
| `role` | Yes | Job title (e.g., "Instructor — Claude & AI Tools") |
| `department` | Yes | Used for filter buttons. Use existing values or add new ones. Current: `Instructors`, `Teaching Assistants`, `Consultants` |
| `bio` | Yes | 1-3 sentences about the person |
| `photo` | No | Path to photo in `images/team/`. Leave `""` for emoji avatar |
| `linkedin` | No | Full LinkedIn URL. Leave `""` to hide the icon |
| `color` | Yes | Card accent color. Options: `blue`, `purple`, `indigo`, `emerald`, `rose`, `amber`, `cyan` |

### Adding a New Department

Just use a new `department` value in team.json — the filter button appears automatically on the team page. No code changes needed.

```json
{ "department": "Advisory Board" }
```

This auto-creates an "Advisory Board" filter button.

---

## Hosting on Cloudflare Pages (Recommended)

### Why Cloudflare Pages?
- Free tier (unlimited sites, unlimited bandwidth)
- Your GitHub repo stays **private** (source code hidden)
- Auto-deploys on every `git push`
- Free SSL certificate
- Global CDN (fast everywhere)
- Custom domain support (aimlengineers.com)

### Setup Steps

1. **Make your GitHub repo private**
   - Go to repo → Settings → Danger Zone → Change visibility → Private

2. **Sign up at [pages.cloudflare.com](https://pages.cloudflare.com)**
   - Use your GitHub account to sign in

3. **Create a new project**
   - Click "Create a project" → "Connect to Git"
   - Select your private repo
   - Build settings:
     - Framework preset: `None`
     - Build command: *(leave empty)*
     - Build output directory: `/` (or `.` — root of repo)
   - Click "Save and Deploy"

4. **Add your custom domain**
   - Go to your project → Custom domains → Add domain
   - Enter `aimlengineers.com`
   - Cloudflare will give you DNS records to update
   - If already using Cloudflare DNS: it's automatic

5. **Done!** Every `git push` to `main` auto-deploys in ~30 seconds.

### Alternative: Netlify

Same concept, slightly different UI:
1. Go to [netlify.com](https://netlify.com)
2. "Add new site" → "Import from Git" → Select repo
3. Build command: empty, Publish directory: `.`
4. Add custom domain in site settings

---

## Local Development

Just open `index.html` in a browser. For the team page to load `team.json`, you need a local server (browsers block fetch from `file://`):

```bash
# Python (any version)
python3 -m http.server 8000

# Then open http://localhost:8000
```

---

## File Sizes

Keep the repo lean for fast deploys:
- Team photos: compress to <100KB each (use [squoosh.app](https://squoosh.app))
- Videos: don't host here — use YouTube/Loom and embed URLs
- Total repo should stay under 50MB ideally
