# $Xorg: Makefile,v 1.5 2000/08/17 19:41:44 cpqbld Exp $
# $Id: Makefile,v 1.5 2005/12/14 23:41:52 alanc Exp $



# $XFree86: xc/Makefile,v 3.28tsi Exp $

# Luna users will need to either run make as "make MAKE=make"
# or add "MAKE = make" to this file.

RELEASE = "Release $(shell cat ../VERSION)"
SHELL = /bin/sh
RM = rm -f
MV = mv
WORLDOPTS =
WIN32WORLDOPTS = -i
TOP = .
CURRENT_DIR = .
CONFIGSRC = $(TOP)/config
IRULESRC = $(CONFIGSRC)/cf
IMAKE = imake
IMAKE_CMD = $(IMAKE) -I$(IRULESRC) $(IMAKE_DEFINES)
MAKE_OPTS = -f xmakefile
MAKE_CMD = $(MAKE) $(MAKE_OPTS)

all:
	@${MAKE} ${MAKE_OPTS} xmakefile-exists || $(MAKE) all-initial
	@${MAKE} ${MAKE_OPTS} $@

all-initial:
	@echo Please use make World, or on NT use nmake World.Win32.
	@echo
	@echo Read the release notes carefully before proceeding.
	@echo Do not name your log file make.log or it will be deleted.

World:
	@echo ""
	@echo Building $(RELEASE).
	@echo ""
	@date
	@echo ""
	if [ ! -f xmakefile ]; then ${MAKE} ${MFLAGS} BuildEnv; fi
	${MAKE} ${MAKE_OPTS} $(MFLAGS) $(WORLDOPTS) World
	@echo ""
	@date
	@echo ""
	@echo Full build of $(RELEASE) complete.
	@echo ""

BuildEnv:
	@if [ -f xmakefile ]; then \
	    ${MAKE} ${MAKE_OPTS} -k distclean || \
	    ${MAKE} ${MAKE_OPTS} -k clean || \
	    $(RM) xmakefile; \
	fi
	@rm -f $(IRULESRC)/date.def; echo "" > $(IRULESRC)/date.def;
	${MAKE} $(MFLAGS) xmakefile
	${MAKE} ${MAKE_OPTS} $(MFLAGS) VerifyOS
	${MAKE} ${MAKE_OPTS} $(MFLAGS) Makefiles
	${MAKE} ${MAKE_OPTS} $(MFLAGS) BOOTSTRAPSUBDIRS= clean
	${MAKE} ${MAKE_OPTS} $(MFLAGS) includes
	${MAKE} ${MAKE_OPTS} $(MFLAGS) depend


.PRECIOUS: Makefile

# This is just a sequence of bootstrapping steps we have to do.
# The steps are listed as separate targets so clearmake can wink in
# the Makefile.proto files.

Makefile::
	$(MAKE) $(MFLAGS) xmakefile

xmakefile: Imakefile
	@if [ -f xmakefile ]; then set -x; \
	 $(RM) xmakefile.bak; $(MV) xmakefile xmakefile.bak; \
	 else exit 0; fi
	@rm -f $(IRULESRC)/date.def; echo "" > $(IRULESRC)/date.def;
	$(IMAKE_CMD) -s xmakefile -DTOPDIR=$(TOP) -DCURDIR=$(CURRENT_DIR)

# don't allow any default rules in this Makefile
.SUFFIXES:
# quiet "make" programs that display a message if suffix list empty
.SUFFIXES: .Dummy

# a copy of every rule that might be invoked at top level

clean:
	    -${MAKE_CMD} ${MAKE_OPTS} $@
	    find config -type f | egrep '.*/Makefile$$' | while read makefile; do rm -f $$makefile; done
	    find lib -type f | egrep '.*/Makefile$$' | while read makefile; do rm -f $$makefile; done
	    find programs -type f | egrep '.*/Makefile$$' | while read makefile; do rm -f $$makefile; done
	    find include -type f | egrep '.*/Makefile$$' | while read makefile; do rm -f $$makefile; done
dangerous_strip_clean:
	    ${MAKE} ${MAKE_OPTS} $@
distclean:
	    -${MAKE} ${MAKE_OPTS} $@
	    $(RM) xmakefile
depend:
	    ${MAKE} ${MAKE_OPTS} $@
Everything:
	    ${MAKE} ${MAKE_OPTS} $@
external.ln:
	    ${MAKE} ${MAKE_OPTS} $@
includes:
	    ${MAKE} ${MAKE_OPTS} $@
install.sdk:
	    ${MAKE} ${MAKE_OPTS} $@
install.ln:
	    ${MAKE} ${MAKE_OPTS} $@
install.man:
	    ${MAKE} ${MAKE_OPTS} $@
install:
	    ${MAKE} ${MAKE_OPTS} $@
Makefiles:
	    ${MAKE} ${MAKE_OPTS} $@
man_keywords:
	    ${MAKE} ${MAKE_OPTS} $@
tags:
	    ${MAKE} ${MAKE_OPTS} $@
VerifyOS:
	    ${MAKE} ${MAKE_OPTS} $@
