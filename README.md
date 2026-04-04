# Personal Website

Built with [Hugo](https://gohugo.io/) and the [LoveIt](https://github.com/dillonzq/LoveIt) theme. Deployed to GitHub Pages automatically on push to `main`.

## Prerequisites

- [Hugo](https://gohugo.io/installation/) (extended edition)
  ```bash
  brew install hugo
  ```

## Local Development

```bash
hugo server -D
```

Open http://localhost:1313 to preview. Changes reload automatically.

## Project Structure

```
content/
  _index.md          # Home page content (renders below the welcome banner)
  about.md           # About page
  posts/             # Blog posts go here
    hello-world.md   # Example post
static/
  profile.jpg        # Profile picture (and any other static files)
assets/
  css/_custom.scss   # Custom CSS overrides
hugo.toml            # Site configuration
```

## Common Tasks

### Edit the home page

Edit `content/_index.md`. The typewriter "Welcome to my website" text is configured in `hugo.toml` under `[params.home.profile]`.

### Edit the about page

Edit `content/about.md`.

### Add a new blog post

Create a new file in `content/posts/`:

```bash
hugo new posts/my-new-post.md
```

This creates a post from the default archetype. Posts with `draft: true` in the front matter are only visible with `hugo server -D` and won't be published.

Front matter options:

```yaml
---
title: "Post Title"
date: 2026-04-03
draft: false
tags: ["tag1", "tag2"]
categories: ["category"]
---
```

### Change site title or author

Edit `hugo.toml` — update `title`, `[params.author]`, and `[params.header.title]`.

### Add social links

In `hugo.toml` under `[params.social]`, fill in your usernames:

```toml
[params.social]
  GitHub = "your-username"
  Linkedin = "your-username"
  X = "your-handle"
  Email = "you@example.com"
```

Then set `social = true` under `[params.home.profile]` to show them on the home page.

### Change the profile picture

Replace `static/profile.jpg` with your new image (keep the same filename, or update the `src` in `content/_index.md`).

### Add navigation menu items

Add entries in `hugo.toml` under `[menu]`:

```toml
[[menu.main]]
  weight = 5
  identifier = "projects"
  name = "Projects"
  url = "/projects/"
```

Then create the corresponding `content/projects.md` or `content/projects/_index.md`.

### Customize CSS

Edit `assets/css/_custom.scss` to override any theme styles.

## Deployment

Pushing to `main` triggers the GitHub Actions workflow (`.github/workflows/deploy.yml`) which builds the site and deploys to GitHub Pages.

In the GitHub repo settings, set **Pages > Source** to **GitHub Actions**.
