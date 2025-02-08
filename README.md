# Locally generate pages

### Install Hugo

https://github.com/gohugoio/hugo/releases/tag/v0.143.1

### Clone This Repo

### Run Hugo Commands

`hugo serve`: serves the pages locally
`hugo new content content/page-name.md`: creates a new page page-name.md  
This will create `page-name.md` at content folder, it's contents would be something like this:
`
+++
date = '2025-02-08T13:01:54-05:00'
draft = true
title = 'New Page'
+++
`

- The `title` is the header at the top of the page.
- You need to change the `draft = true` to `false`
- The page will be available at `http://localhost:1313/new-page/` (or `https://paulinakisselev.com/new-page/` after publishing)
- To add the page to the menu change `hugo.toml` at the root of the site.
In the `hugo.toml` there is a part that looks like this:

```
[menus]
    [[menus.main]]
    name = 'Home'
    pageRef = '/'
    weight = 10

    [[menus.main]]
    name = 'About Me'
    pageRef = 'about-me'
    weight = 20

    [[menus.main]]
    name = 'Blog'
    pageRef = 'posts'
    weight = 30

    [[menus.main]]
    name = 'Contact Me'
    pageRef = 'contact-me'
    weight = 40
```

You need to create a new section with a unique `pageRef` and a unique `weight`. `weight` orders the pages in the menu.

# Changing the Theme

Theme is at `themes\paulina`. The folder you care most should be `layouts` for theme files like the base layout (`baseof.html`), home page (`home.html`), blog posts lists (`list.html`), single page (`single.html`). and parts of pages at `partials` folder, it's pretty self explanatory.

The files like javascripts and css and images are at `content` folder.

# Modifying pages

All pages use [Markdown](https://www.markdownguide.org/tools/hugo/) but you can use HTML too. 

# Adding Pictures to the posts

When you are creating a page that needs to have an image you can put the image same location as the .md file in `content` folder.

# Publishing the site

The `public` folder at the root is the output of `hugo serve` and constantly re-generated when you are changing pages. But you _do not_ check-in the `public` folder (that's why it's at `.gitignore`). The github Actions configuration at `.github` folder runs hugo and creates all pages and it's output is used at github pages site.

So ultimately if you are modifying a single page, then you're just modifying a single .md file at `content` folder. And check-in and push. That's it. Rest is handled by github.
