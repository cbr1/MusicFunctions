#
# $Id: Makefile 347 2006-02-25 23:00:42Z nicb $
#
TARGET=MusicFunctions.pdf
SOURCE=master.tex
DVI=$(SOURCE:.tex=.dvi)
PDF=$(SOURCE:.tex=.pdf)
IDX=$(SOURCE:.tex=.idx)
BIBFILE=$(SOURCE:.tex=.bbl)
MACRODIR=./macros
VPATH=.:$(MACRODIR):graphics
TEXENV=TEXINPUTS="$(MACRODIR):"
DEPENDENCIES=macros.sty MusicFunctions.bib ccnotice.sty \
	commercial.tex introduction.tex society.tex future.tex
TEXCRUFT=$(SOURCE:.tex=.aux) $(SOURCE:.tex=.log) $(SOURCE:.tex=.out)\
         $(SOURCE:.tex=.blg) $(DVI) $(SOURCE:.tex=.toc) $(PDF) missfont.log
#
PDFLATEX=$(TEXENV) pdflatex -file-line-error
LATEX=$(TEXENV) latex
DVI2PDF=dvipdfm
MKIDX=makeindex
MV=mv

$(TARGET):	$(SOURCE) $(DEPENDENCIES)
	$(PDFLATEX) $(SOURCE)
	$(PDFLATEX) $(SOURCE)
#	$(MKIDX) $(IDX)
	$(PDFLATEX) $(SOURCE)
	$(MV) $(SOURCE:.tex=.pdf) $@

clean:
	$(RM) $(TARGET) $(TEXCRUFT)

.PHONY:	clean

.SUFFIXES: .pdf .dvi .tex

%.dvi:	%.tex
	$(LATEX) $(SOURCE)
	$(LATEX) $(SOURCE)
	$(LATEX) $(SOURCE)

%.pdf:  %.tex
	$(DVI2PDF) $(DVI)
