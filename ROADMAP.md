# OpenVis Automation Roadmap

Tracking the steps to bring automated meeting notes, release summaries, and community updates to the OpenVis collab space.

---

## Meeting Notes Automation

Every time a bi-weekly meeting notes file is merged into `main`, a GitHub Actions workflow automatically:

1. Collects releases published across all OpenVis project repos in the past 15 days
2. Posts a GitHub Discussion under the **Meeting Notes** category with the notes + release summary
3. Notifies `#open-visualization` on Slack with the Discussion link

### Prerequisites (one-time, repo admin required)

- [ ] Enable **GitHub Discussions** — repo Settings → General → Features → Discussions
- [ ] Create a **"Meeting Notes"** discussion category (use the _Announcements_ type so only maintainers can post)
- [ ] Add **`SLACK_WEBHOOK`** secret — repo Settings → Secrets and variables → Actions
  - Get the Incoming Webhook URL from the OpenJS Slack workspace admin

### Ongoing workflow (after each bi-weekly)

- [ ] Copy `meetings/TEMPLATE.md` → `meetings/YYYY-MM-DD.md`
- [ ] Fill in the slides link, recording link (if available), and any notes
- [ ] Open a PR and merge it — the workflow handles Discussion + Slack automatically

### Repo list maintenance

The workflow monitors releases from these repos. Update `.github/workflows/post-meeting-notes.yml` if projects join or leave OpenVis:

| Project | Repo |
|---|---|
| deck.gl | [visgl/deck.gl](https://github.com/visgl/deck.gl) |
| kepler.gl | [keplergl/kepler.gl](https://github.com/keplergl/kepler.gl) |
| cosmos.gl | [cosmosgl/graph](https://github.com/cosmosgl/graph) |
| perspective | [perspective-dev/perspective](https://github.com/perspective-dev/perspective) |
| geoda.ai | [GeoDaCenter/geoda](https://github.com/GeoDaCenter/geoda) |

---

## Stretch Goal — Website Auto-Update

After each meeting, automatically open a PR on [openjs-foundation/open-visualization](https://github.com/openjs-foundation/open-visualization) to add the meeting to the blog/news section.

- [ ] Audit the website repo structure to determine the blog/news content format
- [ ] Add a `WEBSITE_PAT` secret (Personal Access Token with `repo` scope on `open-visualization`) to this repo
- [ ] Extend the workflow with a step that opens a PR on the website repo containing a generated blog stub from the meeting notes

---

## Content Backlog

- [ ] Fill in `contribute.md`
- [ ] Fill in `join.md`
- [ ] Fill in `best-practices.md`
- [ ] Add historical meeting notes from 2023–2025 to `meetings/`
- [ ] Expand `media.md` with links to summit talk playlists and slides archives
