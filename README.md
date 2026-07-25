# BFH Muse Tarot

A private digital tarot deck — 78 cards, plus 1080x1920 reel-ready versions for social posts.

Live at **https://bfhmusetarot.barbfh.com** (passcode protected).

## What's here

| Path | What it is |
| --- | --- |
| `index.html` | The whole app: passcode gate, card picker, 1- or 2-card spread, canvas preview, download button |
| `cards/` | 78 card images, 600x1020 PNG |
| `reels/` | 78 reel-format images, 1080x1920 PNG |
| `thumbs/` | 78 thumbnails, 180x306 JPG |
| `cards.json` | Card list — slug, name, group, file paths |
| `card-back.png` | Deck back |
| `contact-sheet.jpg` | Full-deck contact sheet |
| `CNAME` | Custom domain for GitHub Pages |

## Deploy

GitHub Pages, published from the root of `main`. No build step. `.nojekyll` is present so folders and files are served as-is.

## Passcode

The gate checks a SHA-256 hash of the passcode, stores the unlock in `localStorage`, and hides the app until it matches. This keeps the deck away from casual visitors — it is not real authentication, since the image files themselves remain reachable by direct URL. Fine for personal use; if the deck ever needs actual access control, it needs to move behind a host that can authenticate requests.

To change the passcode, replace the `HASH` value in `index.html` with the output of:

```
python3 -c "import hashlib; print(hashlib.sha256('YOUR-NEW-PASSCODE'.encode()).hexdigest())"
```
