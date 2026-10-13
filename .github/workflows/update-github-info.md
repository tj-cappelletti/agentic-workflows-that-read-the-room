---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read

network:
  allowed:
    - github.blog
    - github.com

tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]

safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
    allowed-files:
      - site/content/github-info.md
    draft: false
---

# Update GitHub Info

Keep `site/content/github-info.md` current with practical, developer-focused updates from official GitHub sources.

## Instructions

1. Use GitHub repository API tools to read `notes/mona-notes.md` and `site/content/github-info.md`. Do not use terminal, CLI, bash, or sandboxed commands to read repository guidance or reference files.
2. Use the web-fetch tool to fetch `https://github.blog/latest/` and `https://github.blog/changelog/`.
3. Identify meaningful recent items that fit Mona's editorial guidance. Keep summaries short and practical, prioritize information that helps developers learn GitHub faster, and cite the GitHub Blog or GitHub Changelog source URL for each update.
4. Update only `site/content/github-info.md` with the relevant information. Preserve useful existing content and avoid duplicating items already covered.
5. If there is no meaningful new information, make no change and do not open a pull request.
6. If the file changes, use the `create-pull-request` safe output to open a pull request for Mona to review. Summarize the sources consulted and the changes made in the pull request body.
