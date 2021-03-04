# FILES = $(patsubst %.md, %.docx, $(wildcard *.md))
FILES += $(patsubst %.md, %.pdf, $(wildcard presentation.md))

FILTERS =
PDF_ENGINE =
PDF_OPTIONS =
PDF_FORMAT_OPTIONS = --slide-level=2 --listings

# FILTERS += -F pandoc-citeproc
# FILTERS += -F pandoc-crossref
PDF_ENGINE += --pdf-engine=xelatex
PDF_OPTIONS += --from markdown --to beamer presentation.md --template eisvogel.latex --number-sections

%.docx: %.md
	-pandoc "$<" $(FILTERS) -o "$@"
%.pdf: %.md
	-pandoc "$<" --from markdown --to beamer --template eisvogel.latex --pdf-engine=xelatex --o "$@" --slide-level=2 --listings

%.pdf: %.docx
	-unoconv "$<" "$@"

all: $(FILES)
	@echo $(FILES)

clean:
	-rm $(FILES) *~

cleanall: clean
