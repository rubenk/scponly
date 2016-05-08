ACLOCAL_AMFLAGS = -I m4
AM_CFLAGS = -Wall

confdir = $(sysconfdir)/scponly

bin_PROGRAMS = scponly

scponly_SOURCES = \
	config.h \
	helper.c \
	netbsd_getopt_long.c \
	scponly_getopt.h \
	scponly.c scponly.h

scponly_CPPFLAGS = \
	$(AM_CPPFLAGS) \
	-DDEBUGFILE='"$(confdir)/debuglevel"'

dist_man_MANS = scponly.8

dist_conf_DATA = debuglevel

EXTRA_DIST = \
	AUTHOR \
	BUILDING-JAILS.TXT \
	CONTRIB \
	SECURITY


if ENABLE_CHROOTED_BINARY
install-exec-hook:
	$(MKDIR_P) "$(DESTDIR)$(sbindir)" || exit 1; \
	$(install_sh_PROGRAM) scponly "$(DESTDIR)$(sbindir)/$(CHROOTED_NAME)" || exit 1;

uninstall-hook:
	-rm -f "$(DESTDIR)$(sbindir)/$(CHROOTED_NAME)"
endif

ctags:
	ctags -R .

