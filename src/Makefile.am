srcdir = @srcdir@

pkglib_LTLIBRARIES = ARIB-STD-B24.la
ARIB_STD_B24_la_SOURCES = arib-std-b24.c jis0201.h jis0208.h jisx0213.h
EXTRA_ARIB_STD_B24_la_DEPENDENCIES = iconv/loop.c iconv/skeleton.c gconv.map

pkglibdir = $(libdir)/gconv/aribb24
pkgdatadir = $(libdir)/gconv/aribb24
dist_pkgdata_DATA = gconv-modules

GCONV_LDFLAGS = -shared -module -avoid-version --version-script=gconv.map
ARIB_STD_B24_la_CFLAGS = -DPIC -fPIC
ARIB_STD_B24_la_LDFLAGS = $(GCONV_LDFLAGS) -rpath '$(pkglibdir)' -L$(GCONVSYSDIR) -R $(GCONVSYSDIR) -lJIS -lJISX0213

install-data-hook:
	iconvconfig "$(DESTDIR)$(pkglibdir)"

installcheck-local:
	iconv -l | grep ARIB

uninstall-hook:
	iconvconfig

