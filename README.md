# NightFolio - A Minimal & Dark Hugo Resume Theme

NightFolio is a lightweight Hugo theme designed for showcasing professional resumes and portfolios. It uses Tailwind CSS for styling and contains fully modular sections out of the box.

## Features

- **Minimal design**
- **Fully modular** sections via Hugo partials
- **Responsive** mobile‑first resume
- **Front matter–driven**: edit `content/_index.md` to manage all content

## Preview

[NightFolio](https://cx48.github.io/NightFolio) can be deployed for free using Vercel or GitHub Pages

![NightFolio](https://github.com/cx48/NightFolio/blob/main/static/images/screenshot.png)

## Project Structure

```text
├── assets/
│   ├── css/
│   │   └── style.css        # main stylesheet (custom)
├── content/
│   └── _index.md            # resume front matter & markdown
├── layouts/
│   ├── index.html           # main layout which contains partials
│   └── partials/            # modular section templates
│       ├── header.html
│       ├── summary.html
│       ├── experience.html
│       ├── education.html
│       ├── skills.html
│       ├── certifications.html
│       ├── projects.html
│       ├── awards.html
│       ├── publications.html
│       ├── languages.html
│       ├── hobbies.html
│       ├── references.html
│       ├── metrics.html
│       └── courses.html
├── static/                  # static assets (css, images)
└── README.md                
```

## Front Matter Sections

The **first four** sections are **required** in your `content/_index.md` front matter:

1. **summary**
2. **experience**
3. **education**
4. **skills**

All other sections are **optional**:

- certifications
- projects
- awards
- publications
- languages_spoken
- hobbies
- references
- metrics (core KPIs)
- courses (training)
- blog (articles)
- volunteer
- speaking
- affiliations
- testimonials

If you omit or leave any optional array empty, its section won’t render.

## Local Development (steps will be added soon)

1. **Install Hugo** (v0.112.0+ recommended):

   ```bash
   brew install hugo  # macOS
   choco install hugo-extended  # Windows
   ```

## Build

To generate the static site:

```bash
hugo --minify
```

The output will be in the `public/` directory.

## Deployment

### Vercel

1. Push your repo to GitHub (or GitLab).
2. Sign in to [Vercel](https://vercel.com) and **Import Project**.
3. Select your Hugo repository.
4. Set **Framework Preset** to `Hugo`
5. Ensure **Build Command** is `hugo --minify` and **Publish Directory** is `public`.
6. Click **Deploy**.

### GitHub Pages

#### Option A: Manual

1. Build locally: `hugo --minify`.
2. Commit the `public/` folder to a `gh-pages` branch.
3. In GitHub repo **Settings ▶ Pages**, set source to `gh-pages`.

#### Option B: GitHub Actions

Add `.github/workflows/pages.yml`:

```yaml
name: Deploy Hugo to GitHub Pages
on:
  push:
    branches: [main]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: '0.112.0'
      - name: Build Site
        run: hugo --minify
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          publish_dir: ./public
          github_token: ${{ secrets.GITHUB_TOKEN }}
```

Push to `main` and the site will auto-deploy to `gh-pages`.


> Enjoy your new Hugo resume! Feel free to customize colors, typography, or add new partials as needed. If you run into any issues, please open an issue or PR in this repo.
