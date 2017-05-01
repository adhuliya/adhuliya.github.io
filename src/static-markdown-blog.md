
Creating a Markdown based Static Blog on [github][githubio]
=================

This blogpost describes how you can easily create a [`markdown`][markdown] based static blogging site within minutes.

[markdown]: http://daringfireball.net/projects/markdown/

Github Repository
---------------------

The blog sits in a [GitHub Repository] [githubrepo] and is served directly from there. Thanks to [github.io] [githubio]. Which also means that this site is completely static.

Clone the [GitHub Repository] [githubrepo] to get this whole project.

[githubrepo]: https://github.com/adhuliya/adhuliya.github.io.git
[githubio]: https://pages.github.com/

Structure of the blog
-----------------------

The structure is very simple. The homepage lists all the blogs from latest to oldest, and each blog post resides in its own web page.

Internally, the blog is structured into three top-level folders. The current snapshot is as given below.

    >>PROMPT(5, 2004, 11:17:42) 
    codeman@nintel05: adhuliya.github.io-git $ tree -F
    .
    ├── index.html
    ├── lazynintel.html
    ├── misc/
    │   ├── index.html
    │   └── origo.css
    ├── README.md
    ├── src/
    │   ├── about-this-blog.md
    │   ├── common-footer.html
    │   ├── common-header.html
    │   ├── index.md
    │   ├── lazynintel.md
    │   └── Makefile
    └── static/
        ├── images/
        └── main.css
    
    4 directories, 12 files

The `misc/` folder is a place to put unused but probably useful stuff for the future.

There are primarily two folders `src/` and `static/`. `static/` holds all images, `.css` files and maybe `.js` files in the future.

The `src/` houses the whole site; mostly in markdown format. The markdown files here are compiled into html5 format and placed inside the **parent** (top level) folder. The homepage is described in `index.md` file, which is the only file housing links to all the current blog posts.


How to use?
--------------

* Go to the `src/` folder.

* Create or edit any `<logicalname>.md` file (one post, one file)

* Open the `index.md` file and add the link to the file : `<logicalname>.html`

* run this,

        src/ $ make

  Now all the relevant `.html` files are generated. The name of `.md` files are carried over to `.html` files as-it-is.

* Now the website is ready to be uploaded to the github repo.

* You are done!

You can customize the `static/main.css` file to your liking.


How it works?
-----------------------

The whole site source is in `src/` folder. All posts are maintained in markdown format. Only the `common-header.html` and `common-footer.html` files are pure html5.

The site is generated from all the markdown files and the two html files. The process is as straight forward as, converting the `.md` files to html5 format and sandwiching it between the `common-header.html` and `common-footer.html` files.

The `index.html` is also basically a markdown file built by the ordered concatenation (`cat`) of:

1. `common-header.html`
2. `index.tmp.html` (`$ markdown index.md > index.tmp.html`)
3. `common-footer.html`

Just like every other `.md` (markdown) file. The `make` program takes care of building the full site properly from the `.md` files.

Run the `make` program from within `src/` folder. The `make` program uses the following `Makefile` (as of this writing; for updated version do check the [GitHub Repository] [githubrepo]):

    >>PROMPT(14, 2010, 11:51:06) 
    codeman@nintel05: src $ cat Makefile
    X = $(wildcard *.md)
    Y = $(basename $(X))
    Z = $(addsuffix .html, $(Y))
    HTMLFILES = $(addprefix ../, $(Z))

    all: $(HTMLFILES)

    ../%.html: common-header.html %.md common-footer.html
    	markdown  $(*).md > $(*).tmp.html
    	cat common-header.html $(*).tmp.html common-footer.html > $@
    	rm $(*).tmp.html

    .PHONY: all
    .DEFAULT: all


