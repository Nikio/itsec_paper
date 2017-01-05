# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# Makefile for LaTex
# 2013, Benjamin Kuhnert (benjamin.kuhnert@h-da.de)
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

PROJECT = "paper"
MAINFILE = "$(PROJECT).tex"
EXCLUDE = "./.git"
LATEXOPTIONS = -synctex=1 -interaction=nonstopmode
SPELLCHECK = hunspell
SPELLCHECKARGS = -p . -d en_US,spellcheck

# forced rules
.PHONY: all clean spellcheck

all: $(MAINFILE) bibliography #index

clean:
	find . -path $(EXCLUDE) -prune -o -name '*.4ct' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.4tc' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.acn' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.acr' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.aux' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.bbl' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.bcf' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.blg' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*-blx.bib' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.css' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.dvi' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.glg' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.glo' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.gls' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.html' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.idv' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.idx' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.ilg' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.ind' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.ist' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.lg' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.lof' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.log' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.lol' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.lot' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.lyx' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.nlo' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.out' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '${PROJECT}.odt' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.ps' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.run.xml' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.spellcheck' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.syg' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.syi' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.synctex.gz' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.tdo' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.tmp' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.toc' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.upa' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.upb' -print -exec rm '{}' \;
	find . -path $(EXCLUDE) -prune -o -name '*.xref' -print -exec rm '{}' \;

bibliography:
	pdflatex $(LATEX_OPTIONS) $(MAINFILE)
	pdflatex $(LATEX_OPTIONS) $(MAINFILE)
	biber $(PROJECT)
	pdflatex $(LATEX_OPTIONS) $(MAINFILE)
	pdflatex $(LATEX_OPTIONS) $(MAINFILE)

index:
	makeindex -s $(PROJECT).ist -o $(PROJECT).gls $(PROJECT).glo
	makeindex -s $(PROJECT).ist -o $(PROJECT).acr $(PROJECT).acn
	makeindex -s $(PROJECT).ist -o $(PROJECT).syi $(PROJECT).syg
	makeglossaries $(PROJECT)
	pdflatex $(LATEX_OPTIONS) $(MAINFILE)
	pdflatex $(LATEX_OPTIONS) $(MAINFILE)

$(MAINFILE):
	pdflatex $(LATEX_OPTIONS) $(MAINFILE)
	pdflatex $(LATEX_OPTIONS) $(MAINFILE)

html: $(MAINFILE) index
	htlatex $(LATEX_OPTIONS) $(MAINFILE)

odt: html
	libreoffice --convert-to odt ${PROJECT}.html

spellcheck:
	$(SPELLCHECK) $(SPELLCHECKARGS) -l $(PROJECT).tex | sort | uniq > spellcheck/$(PROJECT).spellcheck

