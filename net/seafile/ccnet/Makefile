# $OpenBSD: Makefile,v 1.10 2016/12/16 08:58:43 kirby Exp $

COMMENT =		framework for writing networked applications in C

GH_PROJECT = 		ccnet

SHARED_LIBS =		ccnet 2.0

# GPLv3+
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB += c crypto event_core event_extra ffi gio-2.0 glib-2.0
WANTLIB += gmodule-2.0 gobject-2.0 iconv intl jansson pcre pthread
WANTLIB += searpc sqlite3 ssl uuid z zdb

MODULES =		lang/python
BUILD_DEPENDS =		devel/libtool \
			lang/vala \
			${MODGNU_AUTOMAKE_DEPENDS} \
			${MODGNU_AUTOCONF_DEPENDS}

LIB_DEPENDS =		databases/libzdb \
			databases/sqlite3 \
			devel/libevent2 \
			sysutils/e2fsprogs \
			net/seafile/libsearpc

USE_GMAKE =		Yes
CONFIGURE_STYLE =	gnu
CONFIGURE_ENV +=	CPPFLAGS=-I${LOCALBASE}/include \
			LDFLAGS=-L${LOCALBASE}/lib
CONFIGURE_ARGS += 	--enable-server \
			--disable-compile-demo

AUTOCONF_VERSION =	2.61
AUTOMAKE_VERSION =	1.9

MODPY_ADJ_FILES = 	tools/ccnet-admin.py

pre-configure:
	cd ${WRKSRC} && env AUTOCONF_VERSION=${AUTOCONF_VERSION} \
		AUTOMAKE_VERSION=${AUTOMAKE_VERSION} autoreconf -fi

.include <bsd.port.mk>
