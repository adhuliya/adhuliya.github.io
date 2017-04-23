# adhuliya.github.io

My Github Blogging Site
-----------------------

A (static-markdown) blogging site built from scratch.

How to use this repo:

* Go to the `src/` folder.
* Create or edit any `<logicalname>.md` file (one post one file)
* Open the `index.md` file and add the link to the file : `<logicalname>.html`
* run

        src/ $ make

* now the website is ready to gitsync. Done!

The `static/main.css` can be edited for custom style.


How things work inside:

The whole site source is in `src/` folder. All posts are maintained in markdown format. Only the common-header.html and common-footer.html files are pure html5.

The site is generated from all the markdown files and the two html files. The process is as straight forward as, converting the `.md` files to html5 format and sandwitching it between the `common-header.html` and `common-footer.html` files. Thats all.

The `index.html` is also basically a markdown file built by the ordered concatication (`cat`) of:

1. `common-header.html`
2. `index.tmp` (`$ markdown index.md > index.tmp`)
3. `common-footer.html`

The `make` program takes care of building the site properly from the `.md` files.


