# Show Your mdBook on GitHub Pages

Let's share your book online with [GitHub](https://github.com/). Remember, if you need help ask [ChatGPT](https://chat.openai.com/chat) or [Google](https://www.google.com/).



First, we need to create a [Git repository](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics) to store our book. Here's what to do:

1. Sign up for a [GitHub account](https://github.com/signup). 
2. Create a [new repository](https://github.com/new) for your book.
3. Add your book director to the repository. [It is hard but you can do it!](https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github#adding-a-local-repository-to-github-using-git).
4. Enter these commands to add your book's files to the repository:
```commandline
git add .
git commit -m "Initial commit"
git push
```
5. Create a GitHub [Action workflow for mdbook](https://github.com/marketplace/actions/mdbook-action).

```text
https://github.com/<username>/<repository-name>/actions
```



5. After the GitHub Actions workflow has run, your book will be available at 
```text
https://<your-username>.github.io/<repository-name>/.
```

Share this link with your friends and family!

### Help! I'm Having Problems

Go to [ChatGPT](https://chat.openai.com/chat) and type what is going wrong. You search for guides on [Google](https://www.google.com/). 

