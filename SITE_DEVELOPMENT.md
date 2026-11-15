# GitHub Pages theme

The site uses a repository-local Jekyll layout and stylesheet. The homepage
includes `README.md`, so changes to the project documentation also update the
site. The README and firmware do not need site-specific markup.

## Local preview

Use Ruby 3.3 and Bundler. The GitHub Pages dependency set cannot run on Ruby 4.0.
On macOS with Homebrew, install Ruby 3.3 alongside the default Ruby, then select
it for the current terminal session:

```sh
brew install ruby@3.3
export PATH="$(brew --prefix ruby@3.3)/bin:$PATH"
hash -r
ruby --version
```

Confirm that the last command prints Ruby 3.3.x before continuing. This does not
change Homebrew's default Ruby or edit your shell configuration. If you use a
Ruby version manager instead, install and select the version in `.ruby-version`.

Install dependencies within this checkout and start the preview:

```sh
BUNDLE_PATH=vendor/bundle bundle install
BUNDLE_PATH=vendor/bundle bundle exec jekyll serve --baseurl ""
```

Bundler may install the version recorded in `Gemfile.lock` and restart itself;
that notice is normal. A Ruby version mismatch means the terminal is still
using another Ruby: repeat the `export PATH` command above and check
`ruby --version` and `command -v bundle`.

Open the printed local URL. To check the production path instead:

```sh
BUNDLE_PATH=vendor/bundle bundle exec jekyll serve
```

Open `http://127.0.0.1:4000/contemp/`.

For a build without the preview server:

```sh
BUNDLE_PATH=vendor/bundle bundle exec jekyll build --trace
```

`Gemfile` pins the GitHub Pages dependency set; `Gemfile.lock` records the
resolved dependencies. Generated output, caches, and installed gems are ignored.

## Customization

- Change project metadata, the repository identity, and the site path in
  `_config.yml`.
- Change colors, the 960 px content width, gutters, or the shared 1 rem paragraph
  and list spacing through the CSS custom properties at the top of
  `assets/css/style.scss`.
- Change the header, footer, and page structure in `_layouts/default.html`.

All sections share the same content column. Below desktop width it contracts to
the viewport with 24 px gutters, or 16 px gutters at 600 px and below. Nested
lists use the same vertical spacing at every depth; tables and code blocks can
scroll within their column.

## Publishing

The canonical repository is `aonanj/contemp`. GitHub Pages builds the repository
root on `main` and publishes
at `https://aonanj.github.io/contemp/`. Merging theme changes into that publishing
source uses the existing Pages deployment flow.
