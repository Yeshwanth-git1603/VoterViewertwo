# Voter Search

In-browser SQLite voter search. No backend. Works on phones.
Per-column dropdown on each search box, AND/OR matching, 1 to 10 boxes.

## IMPORTANT: do not open index.html by double-clicking
It must be served over http, not file://. Otherwise fetch() and sql.js are blocked.

### Test locally
    cd this-folder
    python -m http.server 8000
Then open http://localhost:8000

### Deploy (Vercel via GitHub)
Keep all 3 files at the repo ROOT (not inside a subfolder):
    index.html
    voters.db.gz
    vercel.json
Push to GitHub, import the repo in Vercel. Framework Preset: Other.
Output Directory: empty. Build Command: empty.

## How it works
First visit downloads voters.db.gz (~12MB), decompresses in the browser,
caches it in IndexedDB. Later visits load from cache, offline. Search runs
against in-browser SQLite, ~80ms, all 353k rows.
