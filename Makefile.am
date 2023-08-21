dist_doc_DATA = README.md

bin_PROGRAMS = so-main

so_main_SOURCES = so-main.c

foodir = $(includedir)/foo

foo_HEADERS =
include foo-headers.mk

all-local:
	@set -e; \
	LC_ALL="C"; \
	cd "$(srcdir)"; \
	oldmk="$(abs_srcdir)/foo-headers.mk"; \
	newmk="$(abs_builddir)/foo-headers.mk.$$$$"; \
	for hfile in foo/*.h; do \
	  printf 'foo_HEADERS += %s\n' "$$hfile"; \
	done | sort > "$$newmk"; \
	if cmp "$$oldmk" "$$newmk" > /dev/null 2>&1; then \
	  echo "foo-headers.mk is up to date, nothing to do."; \
	  rm -f "$$newmk"; \
	else \
	  printf "Error: foo-headers.mk and the list of foo/*.h are inconsistent.\n       Update $$oldmk\n       from   $$newmk?\n"; \
	  exit 1; \
	fi
