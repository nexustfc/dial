# TFC dial helper

A one-page site that starts a phone call on iPhone. Nexus Switchboard (a Claude artifact) can't open
`tel:` links from inside the Claude app, but it can open ordinary web links. So a tapped number opens
`https://nexustfc.github.io/dial/#3105550100` (or `#3105550100,204` for an extension), and this page
asks the phone to call it, with a big Call button as a fallback.

- The number sits after `#`, so it is never sent to GitHub's servers, and the page clears it from the address bar.
- The page accepts only digits, an optional leading `+` and one `,extension`. It can only start a call;
  it never sends anyone to another website.
- No TFC data, keys or tracking. Strict Content-Security-Policy, `noindex`, `no-referrer`.
- Public repo because GitHub Pages needs it. Changes to `main` should be reviewed; the main risk is
  someone tampering with this page.

Owner: Andrew (IT). Nexus notes: `tfc-nexus-database/docs/claude-notes/phonesheet.md`.
