# $OpenBSD: Makefile,v 1.32 2017/01/03 18:54:48 shadchin Exp $

COMMENT=		GLib library wrapping libgit2

V=			0.24.4
DISTNAME=		libgit2-glib-$V
REVISION=		1

SHARED_LIBS +=	git2-glib-1.0        3.0      # 0.0

SUBDIR=			sources/libgit2-glib/${V:C/^([0-9]+\.[0-9]+).*/\1/}/
MASTER_SITES=		${MASTER_SITE_GNOME:=${SUBDIR}}
EXTRACT_SUFX=		.tar.xz

MODULES=		lang/python \
			x11/gnome

MODGNOME_TOOLS=		gobject-introspection vala

MODPY_VERSION=          ${MODPY_DEFAULT_VERSION_3}

BUILD_DEPENDS=		devel/py-gobject3${MODPY_FLAVOR}
# MODPY_LIBDIR/gi/overrides/
RUN_DEPENDS=		devel/py-gobject3${MODPY_FLAVOR}
LIB_DEPENDS=		devel/gobject-introspection \
			devel/libgit2/libgit2>=0.24.0

USE_GMAKE=		Yes

WANTLIB += crypto curl ffi gio-2.0 girepository-1.0 git2 glib-2.0
WANTLIB += gmodule-2.0 gobject-2.0 iconv intl m nghttp2 pcre pthread
WANTLIB += ssh2 ssl z

CONFIGURE_STYLE=	gnu

.include <bsd.port.mk>
