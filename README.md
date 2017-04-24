My Github Blogging Site
=======================

It has always been so rewarding reading other netizens blogs, that the only way to repay back is to start the good work yourself.

This blog is dedicated to the idea of *learning by sharing*. Thanks to [`markdown`][markdown], the best blogging language out there.

[markdown]: http://daringfireball.net/projects/markdown/

How to use?
--------------

* Go to the `src/` folder.
* Create or edit any `<logicalname>.md` file (one post one file)
* Open the `index.md` file and add the link to the file : `<logicalname>.html`
* run

        src/ $ make

* now the website is ready to gitsync. Done!

The `static/main.css` can be edited for custom style.


How it works?
-----------------------

The whole site source is in `src/` folder. All posts are maintained in markdown format. Only the `common-header.html` and `common-footer.html` files are pure html5.

The site is generated from all the markdown files and the two html files. The process is as straight forward as, converting the `.md` files to html5 format and sandwiching it between the `common-header.html` and `common-footer.html` files. That's all.

The `index.html` is also basically a markdown file built by the ordered concatenation (`cat`) of:

1. `common-header.html`
2. `index.tmp.html` (`$ markdown index.md > index.tmp.html`)
3. `common-footer.html`

The `make` program takes care of building the full site properly from the `.md` files.


