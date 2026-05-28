# ADA Website

Official website for ADA — the study association based in Deventer.

Built with Rails 8, PostgreSQL, Tailwind CSS v4, Vite + TypeScript, and ViewComponent.

## Local setup

### Prerequisites

- Ruby 3.3.6 (`rbenv install 3.3.6`)
- PostgreSQL running locally
- Node.js 20+

### Steps

```bash
# 1. Clone and enter the repo
git clone git@github.com:CaelusC/ADA-Website.git
cd ADA-Website

# 2. Copy env file and fill in your values
cp .env.example .env

# 3. Install dependencies
bundle install
npm install

# 4. Create and migrate the database
bin/rails db:create db:migrate

# 5. Start the dev server (Rails + Vite + Tailwind)
bin/dev
```

The app will be available at `http://localhost:3000`.

## Tech stack

| Layer      | Technology                    |
|------------|-------------------------------|
| Backend    | Rails 8, PostgreSQL           |
| CSS        | Tailwind CSS v4 (standalone)  |
| JS/TS      | Vite + TypeScript             |
| Components | ViewComponent                 |
| Lint       | RuboCop (rails, performance)  |
| Security   | Brakeman                      |

## Running tests

```bash
bin/rails test
```

## Security scan

```bash
bundle exec brakeman -q
```

## Lint

```bash
bundle exec rubocop
```
