# $OpenBSD: Makefile,v 1.51 2016/09/04 09:47:56 jasper Exp $

COMMENT=		abstraction layer between apps and connection managers

DISTNAME=		telepathy-mission-control-5.16.4

SHARED_LIBS +=  mission-control-plugins 3.0      # 5.1

HOMEPAGE=		http://mission-control.sourceforge.net/

MASTER_SITES=		${MASTER_SITES_TP:=telepathy-mission-control/}

WANTLIB += c dbus-1 dbus-glib-1 gio-2.0 glib-2.0 gmodule-2.0
WANTLIB += gobject-2.0 pcre pthread z telepathy-glib ffi

MODULES=		devel/dconf \
			devel/gettext \
			lang/python

MODPY_RUNDEP=		No

BUILD_DEPENDS=		textproc/libxslt
LIB_DEPENDS=		net/telepathy/telepathy-glib>=0.18.0


# both are dependant
CONFIGURE_ARGS+=	--disable-upower \
			--with-connectivity=no

.include <bsd.port.mk>
