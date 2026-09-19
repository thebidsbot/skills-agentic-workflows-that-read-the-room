---
name: update-github-info
description: Keep the GitHub Info page current with practical, source-backed updates.
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
tools:
  github:
    toolsets: [repos]
  web-fetch:
  edit:
safe-outputs:
  create-pull-request:
    max: 1
    reviewers: [mona]
    allowed-files:
      - site/content/github-info.md
    title-prefix: "[github-info] "
network:
  allowed:
    - github.blog
    - github.com
strict: true
---

# Update GitHub Info

Keep Mona's GitHub Info page current using official GitHub sources.

1. Read `notes/mona-notes.md` and `site/content/github-info.md`.
2. Use the GitHub repository API tools to read any repository guidance or reference files you need. Do not use terminal, CLI, or sandboxed commands for that repository guidance or reference reading.
3. Use the web-fetch tool to read:
   - https://github.blog/latest/
   - https://github.blog/changelog/
4. Identify only concise, practical updates that help developers learn GitHub faster. Prefer information that is new or meaningfully useful, and cite the relevant GitHub Blog or GitHub Changelog source in the content.
5. Update only `site/content/github-info.md`. Preserve its existing structure and editorial angle; do not invent facts or add filler. If there is no worthwhile update, leave the file unchanged.
6. When the file needs an update, use the `create-pull-request` safe output to propose the change for Mona to review. Do not write directly to the default branch. Use a clear PR title and summarize the sources and changes in the PR body.