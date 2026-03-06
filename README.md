# Kicker

A crowdfunding platform where creators launch projects and backers support them in exchange for rewards. Browse by category, search, and manage your projects and backings from a single dashboard.

**Stack:** React, Redux, Rails, PostgreSQL (SQLite in development)

---

## Getting Started

**Prerequisites:** Ruby 3.4+, Node.js 18+, npm. For development without PostgreSQL, the app uses SQLite by default.

```bash
# Backend
bundle install
bundle exec rails db:create
bundle exec rails db:migrate
bundle exec rails db:seed

# Frontend (separate terminal)
npm install
npm run start

# Server (another terminal)
bundle exec rails server
```

Open **http://localhost:3000**.

**Tips:** Use `bundle exec` for all `rails` commands. If the page shows "React is broke!", run `npm run start` at least once to build the JS bundle. On Windows, if PostgreSQL is required, set `username` and `password` in `config/database.yml`.

---

## Features

- Browse and search projects without an account
- Sign up / log in with secure authentication
- Create, edit, and delete projects and rewards
- Back projects and manage backings from your dashboard
- Category discovery and project deadlines with clear status (backer, creator, signed in)

---

## Tech

| Layer    | Tools |
| -------- | ----- |
| Frontend | React, Redux, React Router, Webpack, jQuery/Ajax |
| Backend  | Ruby on Rails, PostgreSQL / SQLite, BCrypt, Active Storage (S3 in production) |

---

## Implementation notes

- **Backing eligibility:** Back button is shown only when the user is signed in, is not the project creator, has not already backed, and the project is still active. Messages explain why backing is disabled when it isn’t allowed.
- **Search:** Query is sent to `/api/projects?query=...`. Backend filters by project title and category name (case-insensitive). Empty or “everything” returns all projects; no results triggers suggested projects on the frontend.

---

## Possible next steps

- Project funded / ended state and messaging
- Richer search filters
- Expanded project edit options
