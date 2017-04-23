X = $(wildcard *.md)
Y = $(basename $(X))
Z = $(addsuffix .html, $(Y))
HTMLFILES = $(addprefix ../, $(Z))

all: $(HTMLFILES)

../%.html: common-header.html %.md common-footer.html
	markdown  $(*).md > $(*).tmp
	cat common-header.html $(*).tmp common-footer.html > $@
	rm $(*).tmp

.PHONY: all
.DEFAULT: all
.PRECIOUS: tmp/%.tmp


