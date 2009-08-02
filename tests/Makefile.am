# Tests environment for the Autoconf Archive.
#
# Copyright (c) 2009 by Francesco Salvestrini
# Licensed under the terms of the GNU General Public License.

CLEANFILES = defs
EXTRA_DIST =

do_subst = sed \
	-e 's,[@]abs_builddir[@],$(abs_builddir),g' \
	-e 's,[@]SHELL[@],$(SHELL),g'

all-local: defs

##
## NOTE:
##     In order to debug the tests during the 'distcheck' target use the
##     following TESTS_ENVIRONMENT:
##
##       TESTS_ENVIRONMENT = testdir=@abs_builddir@ DEBUG=x VERBOSE=x
##
TESTS_ENVIRONMENT = testdir=@abs_builddir@

FAIL_TESTS    =					\
	test-fail

SUCCESS_TESTS =					\
	test-success				\
	test-aclocal				\
	test-autoconf

XFAIL_TESTS = $(FAIL_TESTS)
TESTS       = $(FAIL_TESTS) $(SUCCESS_TESTS)

test-success: $(srcdir)/test-success.in Makefile
	( rm -f $@ $@.tmp && \
	  $(do_subst) < $(srcdir)/test-success.in > $@.tmp && \
	  chmod +x $@.tmp && \
	  chmod a-w $@.tmp && \
	  mv -f $@.tmp $@ ) || { \
		rm -f $@ $@.tmp ; \
		exit 1 ; \
	}
EXTRA_DIST += test-success.in
CLEANFILES += test-success

test-fail: $(srcdir)/test-fail.in Makefile
	( rm -f $@ $@.tmp && \
	  $(do_subst) < $(srcdir)/test-fail.in > $@.tmp && \
	  chmod +x $@.tmp && \
	  chmod a-w $@.tmp && \
	  mv -f $@.tmp $@ ) || { \
		rm -f $@ $@.tmp ; \
		exit 1 ; \
	}
EXTRA_DIST += test-fail.in
CLEANFILES += test-fail

test-aclocal: $(srcdir)/test-aclocal.in Makefile
	( rm -f $@ $@.tmp && \
	  $(do_subst) < $(srcdir)/test-aclocal.in > $@.tmp && \
	  chmod +x $@.tmp && \
	  chmod a-w $@.tmp && \
	  mv -f $@.tmp $@ ) || { \
		rm -f $@ $@.tmp ; \
		exit 1 ; \
	}
EXTRA_DIST += test-aclocal.in
CLEANFILES += test-aclocal

test-autoconf: $(srcdir)/test-autoconf.in Makefile
	( rm -f $@ $@.tmp && \
	  $(do_subst) < $(srcdir)/test-autoconf.in > $@.tmp && \
	  chmod +x $@.tmp && \
	  chmod a-w $@.tmp && \
	  mv -f $@.tmp $@ ) || { \
		rm -f $@ $@.tmp ; \
		exit 1 ; \
	}
EXTRA_DIST += test-autoconf.in
CLEANFILES += test-autoconf

clean-local:
	rm -rf testSubDir-*
