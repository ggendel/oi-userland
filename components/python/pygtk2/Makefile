#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL)". You may
# only use this file in accordance with the terms of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source. A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright (c) 2013 Alexander Pyhalov
#

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		pygtk2
COMPONENT_VERSION=	2.17.0
COMPONENT_PROJECT_URL=	http://www.gnome.org
COMPONENT_SUMMARY=	Python bindings for GTK+
COMPONENT_SRC=		pygtk-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.bz2
COMPONENT_ARCHIVE_HASH=	\
    sha256:6a61817a2e765c6209c72ecdf44389ec134c1ebed1d842408bf001c9321f1400
COMPONENT_ARCHIVE_URL=	http://ftp.gnome.org/pub/GNOME/sources/pygtk/2.17/$(COMPONENT_ARCHIVE)

include $(WS_TOP)/make-rules/prep.mk
include $(WS_TOP)/make-rules/configure.mk
include $(WS_TOP)/make-rules/ips.mk

PATH=/usr/gnu/bin:/usr/bin

CFLAGS+=	-I$(PYTHON_VENDOR_PACKAGES.32)/numpy/core/include

gcc_OPT		= -O2

CONFIGURE_OPTIONS+=	--sysconfdir=/etc
CONFIGURE_ENV+=		PYTHON=$(PYTHON)

COMPONENT_POST_INSTALL_ACTION =  $(GSED) -i -e 's:site-packages:vendor-packages:' \
					 $(PROTO_DIR)/usr/lib/pkgconfig/pygtk-2.0.pc

# common targets
build:		$(BUILD_32)

install:	$(INSTALL_32)

test:		$(NO_TESTS)

include $(WS_TOP)/make-rules/depend.mk
