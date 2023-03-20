# Updating SUMMARY.md

1. Open the [ChatGPT](https://chat.openai.com/chat) website.
2. Copy and paste this into ChatGPT and submit:

```text
I am a 9 year old that wants to make a mdbook SUMMARY.md for a book about pokemon`.
```

3. Open the `mybook/src/SUMMARY.md` file with Notepad.
4. Copy and paste the new text into `SUMMARY.md`.
5. Save and close `SUMMARY.md`.

### Result

```text
That's a great idea! Creating a SUMMARY.md file is an important step in creating an mdbook, and it can help you organize your book's contents.

To get started, you will need to create a new file in your project directory called SUMMARY.md. This file will contain the table of contents for your book, with each chapter or section listed as a link.

Here is an example of what your SUMMARY.md file might look like for a book about Pokemon:
```

```markdown
# Table of Contents

- [Introduction](./introduction.md)
- [What are Pokemon?](./what-are-pokemon.md)
- [Types of Pokemon](./types-of-pokemon.md)
- [Battling and Training](./battling-and-training.md)
- [Legendary Pokemon](./legendary-pokemon.md)
- [Conclusion](./conclusion.md)
```

```text
In this example, each chapter of the book is listed with a link to its corresponding markdown file. The first line of the file is the header, which will be displayed at the top of the table of contents. You can customize this header to fit the title of your book.

Once you have created your SUMMARY.md file, you can use the mdbook build command to generate your book in HTML or PDF format. You can also use the mdbook serve command to view your book in a web browser and make changes to your markdown files in real-time.

I hope this helps you get started with creating your Pokemon book! Good luck and have fun!
```

## Make the Chapters

1. Run `mdbook build` to build the book. This will create the files in the src directory.

```commandline
mdbook serve --open
```

2. A browser window will open [http://localhost:3000]( http://127.0.0.1:3000). This is where you can browse your book before you deploy.


3. This is what the directory structure should look like:

```text
mybook/
├── book.toml
└── src/
    ├── introduction.md
    ├── what-are-pokemon.md
    ├── types-of-pokemon.md
    ├── battling-and-training.md
    ├── legendary-pokemon.md
    └── conclusion.md
```

### Next Step

We are going to update `what-are-pokemon.md` with ChatGPT.
