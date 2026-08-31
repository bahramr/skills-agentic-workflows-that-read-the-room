---
name: update-github-info
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:

permissions:
  contents: read
  pull-requests: read

tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]

network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com

safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
---

# Update GitHub Information

Keep Mona's GitHub information page current using authoritative public sources.

## Instructions

1. Read `notes/mona-notes.md` for Mona's priorities, voice, and repository-specific guidance.
2. Read the existing `site/content/github-info.md` before making changes.
3. Use the web-fetch tool to read external public guidance from these exact URLs:
   - https://github.blog/latest/
   - https://github.blog/changelog/
  - https://awesome-copilot.github.com/workflows/
4. When reading repository guidance or reference files, use the GitHub repository API tools. Do not use terminal commands, CLI tools, or sandboxed commands to read them.
5. Identify relevant, recent GitHub announcements, changelog entries, and Awesome Copilot workflows. Prefer authoritative facts from the fetched pages, preserve useful existing content, and do not invent details.
6. Update only `site/content/github-info.md` with a concise, accurate summary for Mona. Include source links and enough dates or context for Mona to assess freshness.
7. Review the diff for factual accuracy, clarity, and scope. If no meaningful update is needed, make no changes and do not open a pull request.
8. If the file changed, use the `create-pull-request` safe output to open a focused pull request for Mona to review. Summarize what changed and cite the fetched GitHub sources in the pull request body. Do not write directly to `main`.
