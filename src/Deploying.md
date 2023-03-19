# Show Your mdBook on GitHub Pages

Let's share your book online with your
friends and family. I know it is complicated but you can do it!

We are going to use the following tools and platforms:

- [Git](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics): A tool used to store changes to your book.
- [GitHub](https://guides.github.com/activities/hello-world/): A website used to store and share code projects.
- [GitHub Pages](https://pages.github.com/): A free website hosting service provided by GitHub.
- [GitHub Actions](https://docs.github.com/en/actions/learn-github-actions/introduction-to-github-actions): An
  automation tool for tasks like book deployments.

First, we need to create a GitHub repository to store our book. Here's what to do:

1. **Create a GitHub repository**: Sign up for a GitHub account, and create a new repo for your book.
2. **Initialize your book**: Run `git init` to initialize your book as a Git repository.
3. **Create a GitHub Actions workflow**:  Create a new file called `.github/workflows/deploy.yml` in your repository.
   Copy and paste the following code:

```yaml
name: Deploy mdBook site to Pages

on:
  push:
    branches: ["main"]

  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    env:
      MDBOOK_VERSION: 0.4.21
    steps:
      - uses: actions/checkout@v3
      - name: Install mdBook
        run: |
          mkdir mdbook
          curl -sSL https://github.com/rust-lang/mdBook/releases/download/v0.4.27/mdbook-v0.4.27-x86_64-unknown-linux-gnu.tar.gz | tar -xz --directory=./mdbook
          echo `pwd`/mdbook >> $GITHUB_PATH
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v3
      - name: Build with mdBook
        run: mdbook build
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v1
        with:
          path: ./book

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v1
```

4. **Commit and push your changes**: Run the following commands:

```commandline
git add .
git commit -m "Initial commit"
git push -u origin main
```

5. **Access your deployed book**: After the GitHub Actions workflow has run, your book will be available at https://<
   your-username>.github.io/<repository-name>/. Share this link with your friends and family!

That's it! You've deployed your own mdBook to GitHub pages. Congrats!

