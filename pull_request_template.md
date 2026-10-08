## What and why

<!-- One or two sentences: what changes for whom, and why. -->

**ClickUp / issue:** <!-- link to the ClickUp card or GitHub issue -->

## Release note

<!-- One line for Friday's release notes, written for non-engineers.
     Example: "Operators now see the guest's pickup point in the ticket e-mail." -->

## Deploy checklist

- [ ] **No database migration** — or: migration file `migrations/…` must be applied to production **before** this is deployed
- [ ] **No new environment variables** — or: added to the server `.env`: `…`
- [ ] No passwords, keys or tokens in the code (they belong in `.env` on the server)
- [ ] Other repos that must deploy first or together: <!-- none / customer-backend, … -->

## How it was tested

<!-- What you ran or clicked, on which environment. "Not tested" is an allowed answer, but say it. -->

## Screenshots

<!-- For anything a user sees. Delete if not relevant. -->
