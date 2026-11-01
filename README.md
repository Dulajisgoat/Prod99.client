# Prod99 Workspace

The student dashboard for **Prod99**, a student productivity platform by 99 Productions.
Goals, a study timer with Pomodoro, private file storage, community posts with likes,
and JSON backup, wrapped in a burgundy glassmorphism interface over a light and a dark
study-room background.

Single-file front end: plain HTML, CSS and vanilla JavaScript, with Supabase for
authentication, database, storage and live updates. No build step.

## Project structure

```
prod99/
├── dashboard.html        # the whole dashboard (HTML + CSS + JS)
├── assets/
│   ├── css-icon.svg      # CSS3 shield icon (shown next to .css files in Files)
│   ├── bg-light.jpg      # YOU ADD: warm, sunlit study-room background
│   └── bg-dark.jpg       # YOU ADD: dark burgundy study-room background
├── logo-light.png        # YOU ADD (already part of your site): logo used in light mode
├── logo-dark.png         # YOU ADD (already part of your site): logo used in dark mode
├── favicon.ico           # already part of your site
├── README.md
└── .gitignore
```

This repo holds the dashboard. The rest of your site (home page, `/login/`) lives
alongside it in your existing project. Copy `dashboard.html`, `assets/`, `README.md`
and `.gitignore` into that project, or use this folder as the repo root and add your
other pages to it.

### Assets you need to add

The image files were not part of what was handed over, so none are included here.

| File | Used for |
|------|----------|
| `assets/bg-light.jpg` | Page background in light mode |
| `assets/bg-dark.jpg` | Page background in dark mode |
| `logo-light.png`, `logo-dark.png` | Header logo (same paths the dashboard already used) |

If your images use another name or format (for example `.webp`), change the two
variables at the top of the `<style>` block:

```css
--bg-light-img:url("/assets/bg-light.jpg");
--bg-dark-img:url("/assets/bg-dark.jpg");
--bg-pos-light:center center;   /* tune per image if the subject is off-center */
--bg-pos-dark:center center;
```

Until the images exist, the page falls back to a plain burgundy/cream gradient, so
nothing breaks.

## Run locally

The dashboard uses root-absolute paths (`/logo-light.png`, `/login/`, `/assets/...`),
so serve the folder from a web server instead of opening the file directly:

```bash
python3 -m http.server 8080
# then open http://localhost:8080/dashboard.html
```

Without a signed-in Supabase session the page redirects to `/login/`. That is the
existing auth guard and is unchanged.

## Supabase

`dashboard.html` initializes Supabase with the project URL and a **publishable (anon)
key**, exactly as before. That key is designed to be public. Access is controlled by
Row Level Security on your tables and storage policies.

- Never put a **service-role key** in this repo or in any front-end file.
- Keep RLS enabled on `profiles`, `goals`, `study_logs`, `posts` and any tasks table.
- No schema, table names, RPCs (`increment_goal_progress`, `increment_like`) or the
  `user-files` storage bucket were changed by the redesign.
- Real-time updates use the existing `posts-live` channel on the `posts` table.

## Deploy

### Cloudflare Pages (matches your existing setup)

1. Push this repository to GitHub.
2. In Cloudflare: **Workers & Pages → Create → Pages → Connect to Git**, pick the repo.
3. Build settings: framework preset **None**, build command empty, output directory `/`
   (or the folder that contains `dashboard.html`).
4. Deploy. Every push to the production branch redeploys.

If you already have a Cloudflare Pages project for Prod99, add these files to that
project's repository instead of creating a new one.

### GitHub Pages

1. Repository **Settings → Pages**, source: your default branch, folder `/ (root)`.
2. Paths such as `/logo-light.png`, `/assets/...` and `/login/` start at the site root.
   They work on a custom domain or a `<user>.github.io` user site. On a project site
   (`<user>.github.io/<repo>/`) they would point at the wrong place, so use a custom
   domain or change those paths to relative ones.

## Push to GitHub

Replace the placeholders with your own account and repository name:

```bash
git init
git add .
git commit -m "Prod99 dashboard redesign"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

Before the first push, run `git status` and confirm no `.env` files, exports or key
files are staged. `.gitignore` already excludes the common ones.

## What changed in the redesign

- New glass interface, burgundy and cream palette, Inter Tight type.
- Two full-page study-room backgrounds that crossfade with the theme toggle.
  The theme choice is still stored in `localStorage` under `prod99_theme`.
- Welcome screen ("Get Started") and a floating dock (Home, Goals, Study, Files,
  Community) with scroll tracking.
- Profile avatar in the top right with a dropdown that holds the username and Log out.
- Owl mascot removed.
- JavaScript logic is unchanged except for three small edits: the profile dropdown and
  dock scroll tracking were added, liked posts are styled with a `.liked` CSS class
  instead of an inline style, and `.css` files in the Files list show the shield icon.

## Checks that were run

Static checks and a headless-browser pass with Supabase **stubbed out**:

- Every element ID the JavaScript references exists in the HTML; no original ID was removed.
- The JavaScript parses without syntax errors.
- Theme toggle, profile menu open/close (click and Escape) and dock navigation
  behaved as expected; no page errors; no horizontal scroll at 390 px and 768 px.

Not tested against your live Supabase project: sign-in, goals, timer logging, file
upload and download, backup import/export, posts, likes and live updates. The backend
code is the original code, but please click through each feature once after deploying.

## License

Add the license that fits your project.
