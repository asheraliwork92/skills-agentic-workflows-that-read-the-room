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
    - awesome-copilot.github.com
safe-outputs:
  missing-tool: false
  missing-data: false
  noop: false
  report-incomplete: false
  create-pull-request:
    draft: false
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info

Read `notes/mona-notes.md` first. Then use web-fetch to read these sources:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Update `site/content/github-info.md` with the most useful recent GitHub updates and Awesome Copilot workflows for developers. Keep the writing short and practical, follow Mona's editorial guidance, and link to the source for every update based on these sources. Do not add claims that are not supported by the fetched pages.

Only edit `site/content/github-info.md`. If the sources offer no worthwhile updates, leave the file unchanged and do not open a pull request. If you make a meaningful update, use the configured safe output to open one non-draft pull request for Mona to review. Include a concise summary and source links in the pull request description; do not write directly to the default branch.
