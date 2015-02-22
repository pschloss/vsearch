#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.67])
AC_INIT([vsearch], [1.1.1], [torognes@ifi.uio.no])
AM_INIT_AUTOMAKE([subdir-objects])
AC_CONFIG_SRCDIR([src/vsearch.cc])
AC_CONFIG_HEADERS([config.h])

WARN="-Wall -Wsign-compare"
PROFILING="-g"
CXXFLAGS="-O3 -msse2 -mtune=core2"

# Checks for programs.
AC_PROG_CXX
AC_PROG_RANLIB
AC_PROG_INSTALL

# Checks for libraries.
# FIXME: Replace `main' with a function in `-lpthread':
AC_CHECK_LIB([pthread], [pthread_create])

# Checks for header files.
AC_CHECK_HEADERS([getopt.h fcntl.h float.h regex.h ctype.h locale.h limits.h x86intrin.h string.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_C_INLINE
AC_TYPE_SIZE_T
AC_TYPE_UINT32_T

# Checks for library functions.
AC_FUNC_MALLOC
AC_FUNC_STRTOD
AC_CHECK_FUNCS([memmove memcpy posix_memalign])


have_pthreads=no
have_bzip2=no
have_zlib=no
AC_SEARCH_LIBS([pthread_create], [pthread], [have_pthreads=yes])
AC_ARG_ENABLE(bzip2, AS_HELP_STRING([--disable-bzip2], [Disable bzip2 support]))
AS_IF([test "x$enable_bzip2" != "xno"], [
  AC_SEARCH_LIBS([BZ2_bzCompress], [bz2], [have_bzip2=yes])
])

AC_ARG_ENABLE(zlib, AS_HELP_STRING([--disable-zlib], [Disable zlib support]))
AS_IF([test "x$enable_zlib" != "xno"], [
  AC_SEARCH_LIBS([gzoffset], [z], [have_zlib=yes])
])

if test "x${have_pthreads}" = "xyes"; then
  AC_CHECK_HEADERS([pthread.h], [], [have_pthreads=no])
fi

if test "x${have_bzip2}" = "xyes"; then
  AC_CHECK_HEADERS([bzlib.h], [], [have_bzip2=no])
fi

if test "x${have_zlib}" = "xyes"; then
  AC_CHECK_HEADERS([zlib.h], [], [have_zlib=no])
fi

AM_CONDITIONAL(HAVE_BZLIB, test "x${have_bzip2}" = "xyes")
AM_CONDITIONAL(HAVE_ZLIB, test "x${have_zlib}" = "xyes")
AM_CONDITIONAL(HAVE_PTHREADS, test "x${have_pthreads}" = "xyes")
AM_PROG_CC_C_O


AC_SUBST(WARN)
AC_SUBST(PROFILING)

AC_CONFIG_FILES([Makefile
                 src/Makefile
                 man/Makefile])

AC_OUTPUT
