# How we work on Maxtoria code

Short rules for the software team (Hussein Haj Ghazal, Mohammad Abdullrazak, Mohammad Babili). They exist so that anyone can see what changed, why, and what a deploy needs.

## Where work is tracked

- **GitHub Project "Maxtoria Development"**: every piece of engineering work, from Backlog to Done.
- **ClickUp → Development**: requests from other teams and the roadmap. When a ClickUp request is planned, open a GitHub issue for it and paste each link into the other.

## Branches

| Prefix | For |
|---|---|
| `feature/…` | New functionality |
| `fix/…` | Bug fixes |
| `security/…` | Secrets, permissions, vulnerabilities |
| `chore/…` | Dependencies, tooling, clean-up |

Branch from `dev`. Pushing a branch opens a pull request to `dev` automatically; `dev` goes to `main` the same way.

## Commit messages

The first line says **what the change does**, in plain English, as a command. It becomes the pull-request title, so `a` is never a commit message.

- Good: `Show the pickup point in the operator ticket e-mail`
- Good: `Fix double booking when the iyzico callback arrives twice`
- Not useful: `a`, `update`, `fix`, `changes`

Add a blank line and a few lines of *why* when the reason is not obvious.

## Pull requests

- One change per pull request. A pull request that touches finance and SEO is two pull requests.
- Fill in the checklist in the description, especially **migration** and **.env**.
- **One approval from another engineer** before merging to `dev`. Nobody approves their own code.
- The **release note** line is copied into Friday's update for the other teams.

## Database migrations

Migrations are `.sql` files applied by hand. A backend deployed before its migration fails, sometimes on every booking.

1. Mark the pull request: Migration = **Yes** on the project board, and tick the box in the description.
2. Apply the migration to production **before** deploying the backend that needs it.
3. Never apply a migration to production from a local machine running with production `.env` by accident: check which database you are connected to first.

## Secrets

Passwords, API keys, service-account files and tokens never go into the repository. They live in the server's `.env` (or a gitignored file on the server). If one is committed by mistake, it is **rotated**, not just deleted: git history keeps the old value.

## Urgent fixes (P0)

Booking or payment broken, money being lost, security or legal problem. The engineer on support duty that week fixes it the same day, with a `fix/…` branch and a normal pull request; the reviewer reviews it straight away.
