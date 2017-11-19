###################################################
# Makefile
#
# Inspired by:
# https://gist.github.com/kristopherjohnson/7466917
# https://github.com/kjhealy/pandoc-templates/blob/master/examples/Makefile
#
# Run "make" (or "make all") to convert to all other formats
# Run "make clean" to delete converted files
###################################################

## Markdown extension (e.g. md, markdown, mdown).
MEXT = md

## All markdown files in the working directory
SRC = $(wildcard *.$(MEXT))

## Location of Pandoc support files.
PREFIX = pandoc_stuff

## Location of your working bibliography file
BIB = document_refs.bib

## CSL stylesheet (located in the csl folder of the PREFIX directory).
CSL = plos

HTML=$(SRC:.md=.html)
DOCX=$(SRC:.md=.docx)
PDFS=$(SRC:.md=.pdf)
TEX=$(SRC:.md=.tex)

## Options
PANDOC_OPTIONS=--smart --standalone \
--csl=$(PREFIX)/csl/$(CSL).csl \
--bibliography=$(BIB) \
--filter pandoc-citeproc \
--filter pandoc-fignos \
--filter pandoc-eqnos \
--filter pandoc-tablenos \
--variable fontsize=12pt \
--variable papersize=a4 \
--variable colorlinks \

## More Options
PANDOC_HTML_OPTIONS=--to html5 \
--css $(PREFIX)/css/pandoc.css
PANDOC_DOCX_OPTIONS=
PANDOC_PDF_OPTIONS=-H $(PREFIX)/sty/format.sty \
--variable indent \
--variable fontfamily=accanthis \
--variable geometry:"top=1.5cm, bottom=2.5cm, left=1.5cm, right=1.5cm"

all:	$(PDFS) $(HTML) $(TEX) $(DOCX)

pdf:	clean $(PDFS)
html:	clean $(HTML)
tex:	clean $(TEX)
docx:	clean $(DOCX)

%.pdf : %.md
	pandoc $(PANDOC_OPTIONS) $(PANDOC_PDF_OPTIONS) -o $@ $<

%.tex : %.md
	pandoc $(PANDOC_OPTIONS) $(PANDOC_PDF_OPTIONS) -o $@ $<

%.html : %.md
	pandoc $(PANDOC_OPTIONS) $(PANDOC_HTML_OPTIONS) -o $@ $<

%.docx : %.md
	pandoc $(PANDOC_OPTIONS) $(PANDOC_DOCX_OPTIONS) -o $@ $<

clean:
	rm -f *.html *.pdf *.tex *.docx *.odt *.log *.out *.aux *.rtf
