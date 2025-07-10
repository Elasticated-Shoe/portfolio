# Static Blog for GitHub Pages

This is a simple static blog site designed for easy deployment on GitHub Pages. It uses Jekyll, the default static site generator supported by GitHub Pages.

## Features
- Write posts in Markdown (`_posts` folder)
- Simple, modern design
- Easy navigation
- Ready for GitHub Pages deployment

## Getting Started

1. **Write Posts:**
   - Add new Markdown files to the `_posts` directory. Use the format `YYYY-MM-DD-title.md`.
2. **Customize:**
   - Edit `_config.yml` for site settings (title, description, etc).
   - Update the `index.html` and layout files for your style.
3. **Preview Locally:**
   - Install Ruby and Bundler if not already installed.
   - Run `bundle install` to install dependencies.
   - Run `bundle exec jekyll serve` to preview at `http://localhost:4000`.
4. **Deploy:**
   - Push your changes to the `main` or `gh-pages` branch on GitHub.
   - Enable GitHub Pages in your repository settings.


## My React-based CV

You can add your React-based CV here. To do this:

1. Build your React app (e.g., with `npm run build`).
2. Copy the contents of the React build output (usually the `build` or `dist` folder) into a new directory in this repository, such as `/cv` or `/assets/cv`.
3. Link to your CV from your blog or navigation, for example: `[View my CV](/cv/index.html)`.
4. Ensure all asset paths in your React build are relative or correctly configured for GitHub Pages.

---

## Resources
- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages Guide](https://docs.github.com/en/pages)
