# Hoium.me

Personal portfolio website built with Jekyll, based on the [front-cover](https://github.com/dashingcode/front-cover) theme.

**Live site:** [hoium.me](https://www.hoium.me)

---

## Build Instructions

### Prerequisites

1. Install [Homebrew](https://brew.sh)

   ```sh
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. Install [rbenv](https://github.com/rbenv/rbenv)

   ```sh
   brew install rbenv
   ```

3. Install Ruby (version specified in `.ruby-version`)

   ```sh
   rbenv install 3.4.8
   ```

4. Install [Jekyll](https://github.com/jekyll/jekyll)

   ```sh
   gem install jekyll
   ```

### Run Locally

```sh
jekyll serve --incremental
```

Or use the Makefile:

```sh
make serve
```

View the site at [http://localhost:4000](http://localhost:4000)

---

## Configuration

All site content is managed through `_config.yml`. Edit this file to update:

- Personal information (`name`, `description`)
- Social media links (`github_username`, `linkedin_username`, etc.)
- Images (`avatar_img_path`, `front_img_path`)

---

## Deployment

The site deploys automatically to GitHub Pages when changes are pushed to the `main` branch.
