# 11ty Pug Bug Reproduction

This repo demonstrates a bug I've found in 11ty's serve integration with Pug. Updating partials that are included in a Pug template using `include` does not trigger pages using the template to rerender. To reproduce:

```sh
git clone https://github.com/harrislapiroff/11ty-pug-bug
npm install
npx @11ty/eleventy --serve
```

Observe the page at http://localhost:8080/ should have a heading "Hello world!" and content "Change the heading above by editing src/_includes/partial.pug."

Edit the file `src/_includes/partial.pug` to say something else, like "Goodbye world!"

Observe the page in your browser still says "Hello world!" in the header (expected behavior: page should say "Goodbye world!")

Trigger a save of the file `src/_includes/page.pug` (you do not need to make any changes). Observe that the page in your browser now correctly reads "Goodbye world!"