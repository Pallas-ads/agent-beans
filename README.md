# Agent Beans website

The homepage and live demo of Agent Beans, an always-on Meta ads growth team for small businesses and indie developers, built on Meta's Muse models for the Meta Global AI Developer Hackathon.

**Site:** [pallas-ads.github.io/agent-beans](https://pallas-ads.github.io/agent-beans/)

This repository holds only the website. The Agent Beans code lives in its own repository.

## What is here

| Path | Contents |
| --- | --- |
| `site/` | The homepage (a single HTML file), the script that builds the site, and the Google Apps Script that records demo sign-ups in a Google Sheet |
| `web/` | The Agent Beans web app, built in replay mode: it reads a recorded run and changes nothing |
| `replay/northpaw/` | A recorded live run for Northpaw Supply, an online pet store already running ads |
| `replay/beans-active/` | A recorded live run for Beans' Active, a new fitness app with no ad history |
| `.github/workflows/pages.yml` | Builds the site and publishes it to GitHub Pages on every push to `main` |

The homepage embeds each replay at `demo/<run>/`. Because it is the real app, a visitor can click through the Team Room, deliverables, dashboard, ads, memory and harness of each run.

## Build it locally

Requirements: Node 18 or later.

```bash
cd web && npm ci && cd ..
bash site/build.sh
python3 -m http.server 8000 --directory _site
```

Then open http://127.0.0.1:8000.

## Update a replay

A replay is recorded with `pgt replay` from a running Agent Beans server, in the code repository. Copy the `data/` and `media/` folders it writes into `replay/<run>/`. When the app itself has changed, copy the code repository's `web/` folder here as well, so the replay build reads the files the new export writes.

## Data and license

Everything in the demo is synthetic sandbox data. The site calls no model and holds no key or real ad account ID, and `pgt replay` refuses to export anything that is not sandbox data.

The code in this repository is MIT licensed.

**Built with Muse Spark Open.** The recorded runs were made with Muse Spark Open, used under the Muse Model License, which asks for this notice.
