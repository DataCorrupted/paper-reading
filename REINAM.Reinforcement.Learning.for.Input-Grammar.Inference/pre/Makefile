# You may override this variable from the command line. E.g.:
# make target=foo
# make clean target=foo
slides = slides
tex = pdflatex

.PHONY : clean all

all : clean $(patsubst %,%.pdf,$(target)) slides.pdf

clean :
	for i in aux log bbl blg bcf out run.xml pdf auxlock fdb_latexmk fls tdo synctex\(busy\) nav snm toc vrb; do \
		rm -f $(patsubst %,%.$$i,$(target)); \
		rm -f $(patsubst %,%.$$i,$(slides)); \
	done
	-rm -f *~
	rm plots/cache/main-figure* -rf

slides.pdf: $(slides).tex 
	$(tex) $<
	biber $(slides)
	$(tex) $<
	