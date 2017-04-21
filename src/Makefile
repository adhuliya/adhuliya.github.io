X = $(wildcard *.md)
Y = $(basename $(X))
Z = $(addsuffix .html, $(Y))
HTMLFILES = $(addprefix ../, $(Z))

all: $(HTMLFILES)

tmp/%.tmp: %.md
	markdown $< > $@

../%.html: common-header.html tmp/%.tmp common-footer.html
	cat $+ > $@

.DEFAULT: all
.PRECIOUS: tmp/%.tmp


