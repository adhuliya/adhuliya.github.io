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


