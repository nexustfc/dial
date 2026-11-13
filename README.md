# TFC dial helper

A one-page site that starts a phone call on iPhone. Nexus Switchboard (a Claude artifact) can't open
`tel:` links from inside the Claude app, but it can open ordinary web links. So a tapped number opens
`https://nexustfc.github.io/dial/#3105550100` (or `#3105550100,204` for an extension), and this page
shows a big Call button (iPhone needs a tap before it will offer to call, and won't let the page close itself, even when opened by a script; tested 2026-11-13). Switchboard sends
`#t=<number>&n=<name>&c=<company>&k=<number type>` so the page can show who is being called. It never
sends the call's Re: line or anything else from the call record.

- The number sits after `#`, so it is never sent to GitHub's servers, and the page clears it from the address bar.
- The page accepts only digits, an optional leading `+` and one `,extension`. It can only start a call;
  it never sends anyone to another website.
- No TFC data, keys or tracking. Strict Content-Security-Policy, `noindex`, `no-referrer`.
- Public repo because GitHub Pages needs it. Changes to `main` should be reviewed; the main risk is
  someone tampering with this page.

Owner: Andrew (IT). Nexus notes: `tfc-nexus-database/docs/claude-notes/phonesheet.md`.

Found 2026-11-13: the Claude iPhone app passes the part after `#` along re-encoded (`%3D` for `=`, `%26` for `&`),
so the page undoes up to three layers of encoding before reading it. If it still can't read a link, a small grey
line shows what arrived (lengths and a masked outline only: digits as 9, letters as a).
