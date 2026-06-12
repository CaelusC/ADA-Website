# ADA Website

Website for ada (Studievereniging voor ICT), the student association at Saxion in Deventer.

Built with Ruby on Rails 8, PostgreSQL, Tailwind CSS v4 and ViewComponent.

## Prerequisites

You need these:

- Ruby 3.3.6
- PostgreSQL
- Bundler

## Setup

<<<<<<< HEAD
Clone the repo and cd into it, then:

```bash
bundle install
```

Copy the example env file:

```bash
cp .env.example .env
```

Edit `.env` if your PostgreSQL setup needs a username/password. By default it thinks you're running Postgres locally with no auth.

Create and migrate the database:

```bash
rails db:create
rails db:migrate
```

Seed some data:

```bash
rails db:seed
```

Start the server:

```bash
rails server
```

## Running tests

```bash
bundle exec rspec
```

## Linting

```bash
bundle exec rubocop
bundle exec brakeman -q
```

Fix rubocop offenses automatically with:

```bash
bundle exec rubocop -a
```

=======
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


>>>>>>> parent of 17a4bc7 (Merge pull request #22 from CaelusC/feat/dip-setup)
## Stack

- **Rails 8.1** — backend framework
- **PostgreSQL** — database
- **Tailwind CSS v4** — styling
- **ViewComponent** — reusable UI components
- **Hotwire (Turbo + Stimulus)** — frontend reactivity without React
- **RSpec** — tests
- **Brakeman** — security scanning
- **RuboCop** — linting
