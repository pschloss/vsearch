bin_PROGRAMS = vsearch

vsearch_SOURCES = cityhash/city.cc \
	align.cc align_simd.cc arch.cc bitmap.cc chimera.cc cluster.cc\
	db.cc dbindex.cc derep.cc maps.cc mask.cc minheap.cc msa.cc \
	query.cc results.cc search.cc searchcore.cc showalign.cc shuffle.cc \
	sortbylength.cc sortbysize.cc unique.cc userfields.cc util.cc vsearch.cc \
	allpairs.cc linmemalign.cc \
        cityhash/city.h cityhash/citycrc.h cityhash/config.h \
	align.h align_simd.h arch.h bitmap.h chimera.h cluster.h cpu.h db.h \
	dbindex.h derep.h maps.h mask.h minheap.h msa.h query.h results.h \
	search.h searchcore.h showalign.h shuffle.h sortbylength.h \
	sortbysize.h unique.h userfields.h util.h vsearch.h \
	allpairs.h linmemalign.h string.h

vsearch_CXXFLAGS = -I${srcdir}/cityhash @WARN@ @PROFILING@
vsearch_LDADD = libcpu_ssse3.a libcpu_sse2.a
noinst_LIBRARIES = libcpu_ssse3.a libcpu_sse2.a
libcpu_ssse3_a_SOURCES = cpu.cc
libcpu_ssse3_a_CXXFLAGS = -mssse3 -DSSSE3 -I${srcdir}/cityhash @WARN@ @PROFILING@
libcpu_sse2_a_SOURCES = cpu.cc
libcpu_sse2_a_CXXFLAGS = -I${srcdir}/cityhash @WARN@ @PROFILING@
