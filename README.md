# ADA Website

Official website for sv-ADA (Studievereniging), the ICT student association at Saxion University of Applied Sciences in **Deventer**.

Built with Ruby on Rails 8, PostgreSQL 17, Tailwind CSS v4, ViewComponent, and Hotwire.

## Setup

Clone the repo:

```bash
git clone https://github.com/CaelusC/ADA-Website.git
cd ADA-Website
```

Copy the env file:

```bash
cp .env.example .env
```

Generate a secret key and paste it into `.env` as `SECRET_KEY_BASE`:

```bash
docker compose run --rm web rails secret
```

Start everything:

```bash
docker compose up --build
```

First run takes a few minutes while Docker pulls images and installs gems. After that it's fast.

`localhost:3000`.

## Daily workflow

```bash
docker compose up          # Start the App
docker compose down        # Stop everything
docker compose down -v     # Stop and wipe the Database
```

Running Rails commands inside Docker:

```bash
docker compose run --rm web rails db:seed
docker compose run --rm web rails generate model Thing name:string
docker compose run --rm web rails console
```

---

## Environment variables

Copy `.env.example` to `.env` and fill in the values. Never commit `.env`.

| Variable | Description |
|---|---|
| `POSTGRES_USER` | Database username |
| `POSTGRES_PASSWORD` | Database password |
| `POSTGRES_DB` | Database name |
| `DATABASE_URL` | Full PostgreSQL connection string |
| `RAILS_ENV` | Set to `development` locally |
| `SECRET_KEY_BASE` | Run `rails secret` (output is the secret) |

---

## Testing

```bash
docker compose run --rm web bundle exec rails test
```

---

## Linting and security

```bash
docker compose run --rm web bundle exec rubocop
docker compose run --rm web bundle exec rubocop -a   # Auto fixes, use it with caution pliz
docker compose run --rm web bundle exec brakeman -q
```

---

## Branch workflow

| Branch | Purpose |
|---|---|
| `main` | Production ready code only. (Later will Autodeploy from here) |
| `develop` | Integration branch. All features merge here first |
| `your-feature-branch` | Cut from **develop**, PR back into **develop** |


## Stack

| | Tool | Why |
|---|---|---|
| Framework | Rails 8.1 | Backend, routing, ORM |
| Database | PostgreSQL 17 | Primary datastore |
| Styling | Tailwind CSS v4 | CSS |
| Components | ViewComponent | Reusable, testable UI components |
| Frontend | Hotwire (Turbo + Stimulus) | Reactivity without a JS framework |
| Testing | Minitest | Built in tester |
| Security | Brakeman | Static analysis for Rails vulnerabilities |
| Linting | RuboCop | Ruby style enforcement |
| Deployment | Kamal | Docker-based deployment to VPS |
