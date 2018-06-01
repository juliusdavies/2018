# to compile the paper



all:  single





single:  bib
	pdflatex thesis
#	dvips 000_main.dvi -t letter -o 2011-jese-bertillonage.ps
#	ps2pdf -dSubsetFonts=true -dEmbedAllFonts=true -dCompatibilityLevel=1.4 -dPDFSETTINGS=/prepress -sPAPERSIZE=letter 2011-jese-bertillonage.ps 2011-jese-bertillonage.pdf 

bib:
	bibtex thesis 

clean:
	\rm -f  ./*~ ./*.blg ./*.bbl ./*.aux ./*.log ./*.dvi ./*.ps ./*.pdf ./semantic.cache
	find -iname *.aux -execdir rm {} \; 

PAPER=thesis
#what's the provenance of this block?
pdf:  pdfbib
	pdflatex thesis
	pdflatex thesis
	gs -q -dNOPAUSE -dBATCH -dPDFSETTINGS=/prepress \
              -dDownsampleColorImages=false -dAutoFilterColorImages=false  \
              -dColorImageFilter=/FlateEncode -sDEVICE=pdfwrite -sOutputFile=$(PAPER)-embed.pdf \
	      $(PAPER).pdf
	cp $(PAPER)-embed.pdf $(PAPER).pdf

pdfbib:
	pdflatex thesis 
	bibtex   thesis 
