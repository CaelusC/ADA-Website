# ADA Website

Website for ada (Studievereniging voor ICT), the student association at Saxion in Deventer.

Built with Ruby on Rails 8, PostgreSQL, Tailwind CSS v4 and ViewComponent.

## Prerequisites

You need these:

- Ruby 3.3.6
- PostgreSQL
- Bundler

## Setup

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

## Stack

- **Rails 8.1** — backend framework
- **PostgreSQL** — database
- **Tailwind CSS v4** — styling
- **ViewComponent** — reusable UI components
- **Hotwire (Turbo + Stimulus)** — frontend reactivity without React
- **RSpec** — tests
- **Brakeman** — security scanning
- **RuboCop** — linting
