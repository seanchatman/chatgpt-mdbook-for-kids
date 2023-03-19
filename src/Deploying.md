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
name: Deploy
on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write  # To push a branch 
      pull-requests: write  # To create a PR from that branch
    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: 0
      - name: Install mdbook
        run: |
          mkdir mdbook
          curl -sSL https://github.com/rust-lang/mdBook/releases/download/v0.4.27/mdbook-v0.4.27-x86_64-unknown-linux-gnu.tar.gz | tar -xz --directory=./mdbook
          echo `pwd`/mdbook >> $GITHUB_PATH
      - name: Deploy GitHub Pages
        run: |
          mdbook build
          git worktree add gh-pages
          git config user.name "Deploy from CI"
          git config user.email ""
          cd gh-pages
          git update-ref -d refs/heads/gh-pages
          rm -rf *
          mv ../book/* .
          git add .
          git commit -m "Deploy $GITHUB_SHA to gh-pages"
          git push --force --set-upstream origin gh-pages
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

