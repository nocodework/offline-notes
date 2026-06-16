# Contributing

Thanks for considering a contribution. This project is deliberately tiny and dependency-free, and the goal is to keep it that way.

## Ground rules

- **One file.** The whole app lives in `index.html` — HTML, CSS, and vanilla JS. No build step, no bundler, no npm, no framework.
- **Zero runtime dependencies.** No CDN links, no web fonts, no analytics. The page must make **0 network requests** so it keeps working fully offline. PRs that add a network call will be declined.
- **Notes are user content.** Anything rendered from a note must be HTML-escaped first. Don't introduce a path that puts unescaped note text into `innerHTML`.

## Running it

There's nothing to install. Open `index.html` in a browser, edit the file, refresh.

## Before opening a PR

- Test by hand: write Markdown and watch the live highlight, switch Write / Split / Read, create and delete notes, search, toggle the theme, export `.md` and `.html`, import a `.md` file, reload (autosave).
- Confirm there are still **0 network requests** (DevTools → Network → reload).
- Keep the diff focused and describe what changed and why.

## Ideas that fit

- Markdown parser fixes and more syntax (tables, footnotes)
- Accessibility and keyboard improvements
- Better mobile interactions
- Performance with many or very long notes

## Ideas that don't fit

- Anything requiring a server, account, or network call
- Heavy libraries or a build pipeline

By contributing you agree your work is licensed under the project's [MIT License](LICENSE).
