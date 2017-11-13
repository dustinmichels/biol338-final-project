# all: document_ms.pdf document_ms.doc

# document_ms.doc: document_ms.md document_refs.bib
#     pandoc -H format.sty -V fontsize=12pt --bibliography document_refs.bib --csl=ecology.csl document_ms.md -o document_ms.doc

# document_ms.pdf: document_ms.md document_refs.bib
#     pandoc -H format.sty -V fontsize=12pt --bibliography document_refs.bib --csl=ecology.csl document_ms.md -o document_ms.pdf

all: writeup.pdf writeup.docx

writeup.docx: writeup.md
	pandoc -S -o writeup.docx \
	--filter pandoc-citeproc \
	--filter pandoc-fignos \
	--filter pandoc-eqnos \
	--filter pandoc-tablenos \
	--variable fontsize=12pt \
	--variable papersize=a4paper \
	-H pandoc/format.sty \
	writeup.md

writeup.pdf: writeup.md
	pandoc -S -o writeup.pdf \
	--filter pandoc-citeproc \
	--filter pandoc-fignos \
	--filter pandoc-eqnos \
	--filter pandoc-tablenos \
	--variable fontsize=12pt \
	--variable papersize=a4paper \
	-H pandoc/format.sty \
	writeup.md

# document_ms.pdf: writeup.md
# 	pandoc -S -o document_ms.pdf \
# 	--filter pandoc-citeproc \
# 	--filter pandoc-fignos \
# 	--filter pandoc-eqnos \
# 	--filter pandoc-tablenos \
# 	--variable classoption=twocolumn \
# 	--variable papersize=a4paper \
# 	-H pandoc/format.sty \
# 	writeup.md