SUBDIRS = completions test

sysconf_DATA = bash_completion

profiledir = $(sysconfdir)/profile.d
profile_DATA = bash_completion.sh

bash_completion.sh: bash_completion.sh.in Makefile
	sed -e 's|@sysconfdir[@]|$(sysconfdir)|' <$(srcdir)/$@.in >$@

CLEANFILES = bash_completion.sh

EXTRA_DIST = CHANGES $(sysconf_DATA) bash_completion.sh.in

install-data-hook:
	tmpfile=`mktemp $${TMPDIR:-/tmp}/bash_completion.XXXXXX` && \
	sed -e 's|=/etc/bash_completion|=$(sysconfdir)/bash_completion|' \
		$(DESTDIR)$(sysconfdir)/bash_completion > $$tmpfile && \
	mv $$tmpfile $(DESTDIR)$(sysconfdir)/bash_completion
