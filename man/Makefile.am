dist_man_MANS = vsearch.1
if HAVE_PS2PDF
doc_DATA = vsearch_manual.pdf

vsearch_manual.pdf: vsearch.1
	man -t ./vsearch.1 | ps2pdf -sPAPERSIZE=a4 - vsearch_manual.pdf

CLEANFILES=vsearch_manual.pdf
endif
