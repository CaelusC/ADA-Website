# ADA Website

Official website for sv-ADA (Studievereniging), the ICT student association at Saxion University of Applied Sciences in **Deventer**.

Built with Ruby on Rails 8, PostgreSQL 17, Tailwind CSS v4, ViewComponent, and Hotwire.

## Setup

### Prerequisites

You need **Docker** and **Ruby 3.3.6** installed locally (Ruby is required to run DIP).

Check your Ruby version:

```bash
ruby -v
```

If you don't have Ruby 3.3.6, install it with [rbenv](https://github.com/rbenv/rbenv):

```bash
# macOS
brew install rbenv ruby-build
rbenv install 3.3.6
rbenv global 3.3.6

# Windows (WSL2 recommended — run these inside WSL)
sudo apt update && sudo apt install -y rbenv ruby-build
rbenv install 3.3.6
rbenv global 3.3.6
```

Then install [DIP](https://github.com/bibendi/dip):

```bash
gem install dip
```

### First time setup

Clone the repo and provision everything in one command:

```bash
git clone https://github.com/CaelusC/ADA-Website.git
cd ADA-Website
dip provision
```

`dip provision` will:
1. Copy `.env.example` to `.env`
2. Build the Docker image
3. Create and migrate the database

Start the app:

```bash
dip up
```

`localhost:3000`.

---

## Daily workflow

```bash
dip up                 # Start the app
dip down               # Stop everything
dip down volumes       # Stop and wipe the database
```

---

## Running commands

With DIP (recommended):

```bash
dip rails db:seed
dip rails generate model Thing name:string
dip rails console
dip test
dip rubocop
dip rubocop fix
dip brakeman
```

Without DIP:

```bash
docker compose run --rm web bundle exec rails db:seed
docker compose run --rm web bundle exec rails test
docker compose run --rm web bundle exec rubocop
docker compose run --rm web bundle exec brakeman -q
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

---

## Branch workflow

| Branch | Purpose |
|---|---|
| `main` | Production ready code only. (Later will Autodeploy from here) |
| `develop` | Integration branch. All features merge here first |
| `your-feature-branch` | Cut from **develop**, PR back into **develop** |

---

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
