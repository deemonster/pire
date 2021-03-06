AC_PREREQ([2.60])
AC_INIT([pire], [0.0.4], [dprokoptsev@yandex-team.ru])
AM_INIT_AUTOMAKE([foreign -Wall])
AC_CONFIG_SRCDIR([pire/classes.cpp])
AC_CONFIG_HEADERS([config.h.in])
AC_CONFIG_MACRO_DIR([m4])

AC_LANG_CPLUSPLUS

# Require neccessary binaries to build ourselves
AC_PROG_CXX
AC_PROG_CC
AC_PROG_LEX
AC_PROG_YACC
AC_PROG_LIBTOOL

# Just for conscience' sake
AC_CHECK_HEADERS([stdlib.h stdint.h string.h sys/time.h])
AC_HEADER_STDBOOL
AC_C_INLINE
AC_TYPE_SIZE_T
AC_CHECK_TYPES([ptrdiff_t])
AC_FUNC_ERROR_AT_LINE
AC_FUNC_MALLOC
AC_CHECK_FUNCS([memset strchr])

AC_C_BIGENDIAN

AC_CHECK_ALIGNOF(size_t)
AC_CHECK_ALIGNOF(uint64_t)

# Optional features
AC_ARG_ENABLE([extra], AS_HELP_STRING([--enable-extra], [Add extra functionality (capturing scanner, etc...)]))
AC_ARG_ENABLE([debug], AS_HELP_STRING([--enable-debug], [Make Pire dump all constructed FSMs to std::clog (useless unless debugging Pire)]))
AC_ARG_ENABLE([checked], AS_HELP_STRING([--enable-checked], [Enable asserts]))
AM_CONDITIONAL([ENABLE_EXTRA], [test x"$enable_extra" = xyes])
AM_CONDITIONAL([ENABLE_DEBUG], [test x"$enable_debug" = xyes])
AM_CONDITIONAL([ENABLE_CHECKED], [test x"$enable_checked" = xyes])

AC_CONFIG_FILES([
	Makefile
	pire/Makefile
	tests/Makefile
	pkg/Makefile
	tools/Makefile
	tools/bench/Makefile
	samples/Makefile
	samples/inline/Makefile
	samples/blacklist/Makefile
	samples/pigrep/Makefile
])
AC_OUTPUT_COMMANDS([sed 's/#define \([A-Z]\)/#define PIRE_\1/' < config.h.in > pire/config.h])
AC_OUTPUT
