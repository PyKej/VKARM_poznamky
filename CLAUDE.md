# VKARM notes

Study notes for the VKARM course credit test (control theory: Laplace transform, transfer and step response functions, differential equations, RC circuits, block diagrams, practice test).

Language: all repo files (this file, README, code comments) are in **English**. Only the website content and math explanations are in **Slovak**.

## Files

- `vkarm_poznamky.html`: the main file, always identical to the artifact. The whole "Zápočet VKARM" page in one HTML file (inline CSS and JS). Math is LaTeX for MathJax 3: inline `\( ... \)`, display `\[ ... \]`. Font is IBM Plex from Google Fonts. Chapters are numbered 01–06; worked examples (`.vzor`) and exercise cards (`.ex`) get `KK.NN` numbers from JS in document order.
- `artifact.json`: link to the claude.ai artifact (slug, URL, last synced version, sharing mode). It is in `.gitignore`, so a fresh clone lacks it. Recreate it by calling `get_artifact` with the artifact URL (gives slug and version) and comparing the content with `vkarm_poznamky.html`.

## Syncing with the claude.ai artifact

The local `vkarm_poznamky.html` and the artifact https://claude.ai/artifact/Qk5dMpkMoGjaWNG5aepegS must always have the same content. On **every** page change:

1. **Before editing**, call `get_artifact` with the slug from `artifact.json`. If the live version differs from `version` in `artifact.json`, someone edited the artifact on claude.ai. Fetch it with `read_artifact` first, take the HTML from between the `untrusted-document-…` wrapper tags (they don't belong in the file), overwrite `vkarm_poznamky.html` with it and show the user `git diff`. Only then continue.
2. Edit `vkarm_poznamky.html` locally (Edit).
3. Publish with `publish_files`: `files: [{as: "index.html", path: <absolute path to vkarm_poznamky.html>}]`, `slug` and `base_version` from `artifact.json`. The artifact is **public**, so also pass `shared_live: "public"` and `artifact_title: "Zápočet VKARM"`. Don't pass `title` unless renaming.
4. Write the new version from the result into `version` in `artifact.json`.

If publishing fails with a version conflict, go back to step 1. The user gave standing permission to publish every change right away; keep in mind anyone with the link sees it.

## How to respond

- Chat replies short, in English. The artifact matters, not the chat.
- A question about a math block/problem → write the explanation **into the artifact right at that problem** (in Slovak, matching the page style), then sync as above. In chat, only say briefly what was added and where (problem number, e.g. 03.04).
- Only when the user explicitly says "explain in chat" / "vysvetli v chate", explain in chat, in Slovak, and add nothing to the artifact.

## Git

Commit only when the user asks.
