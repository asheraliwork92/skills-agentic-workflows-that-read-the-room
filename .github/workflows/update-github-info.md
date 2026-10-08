---
name: update-github-info
description: Refresh the GitHub Info page with practical updates from GitHub Blog sources.
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    draft: false
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info

Read `notes/mona-notes.md` first. Then use web-fetch to read both:

- https://github.blog/latest/
- https://github.blog/changelog/

Update `site/content/github-info.md` with the most useful recent GitHub updates for developers. Keep the writing short and practical, follow Mona's editorial guidance, and link to the GitHub Blog or Changelog source for every update based on those sources. Do not add claims that are not supported by the fetched pages.

Only edit `site/content/github-info.md`. If the sources offer no worthwhile updates, leave the file unchanged and use `noop` with a brief explanation. If you make a meaningful update, use the configured safe output to open one non-draft pull request for Mona to review. Include a concise summary and source links in the pull request description; do not write directly to the default branch.
