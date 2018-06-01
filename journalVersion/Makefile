# to compile the paper



all:  single





single:  bib
	pdflatex 000_main
#	dvips 000_main.dvi -t letter -o 2011-jese-bertillonage.ps
#	ps2pdf -dSubsetFonts=true -dEmbedAllFonts=true -dCompatibilityLevel=1.4 -dPDFSETTINGS=/prepress -sPAPERSIZE=letter 2011-jese-bertillonage.ps 2011-jese-bertillonage.pdf 

bib:
	bibtex 000_main

clean:
	\rm -f  ./*~ ./*.blg ./*.bbl ./*.aux ./*.log ./*.dvi ./*.ps ./*.pdf ./semantic.cache

PAPER=000_main
#what's the provenance of this block?
pdf:  pdfbib
	pdflatex 000_main
	pdflatex 000_main
	gs -q -dNOPAUSE -dBATCH -dPDFSETTINGS=/prepress \
              -dDownsampleColorImages=false -dAutoFilterColorImages=false  \
              -dColorImageFilter=/FlateEncode -sDEVICE=pdfwrite -sOutputFile=$(PAPER)-embed.pdf \
	      $(PAPER).pdf
	cp $(PAPER)-embed.pdf $(PAPER).pdf

pdfbib:
	pdflatex 000_main
	bibtex 000_main
