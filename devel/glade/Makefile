# $OpenBSD: Makefile,v 1.72 2016/04/25 16:25:23 jasper Exp $

COMMENT=	user interface builder for the gtk+3 toolkit

GNOME_VERSION=	3.20.0
GNOME_PROJECT= 	glade

CATEGORIES=	devel

SHARED_LIBS +=  gladeui-2                 1.0 # 0.0

HOMEPAGE=	http://glade.gnome.org/

MAINTAINER=	Jasper Lievisse Adriaanse <jasper@openbsd.org>, \
		Antoine Jacoutot <ajacoutot@openbsd.org>

# GPLv2 - LGPLv2
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB += ${MODPY_WANTLIB}
WANTLIB += ICE SM X11 Xcomposite Xcursor Xdamage Xext Xfixes Xi Xinerama
WANTLIB += Xrandr Xrender atk-1.0 atk-bridge-2.0 atspi c cairo
WANTLIB += cairo-gobject dbus-1 epoxy expat ffi fontconfig freetype
WANTLIB += gdk-3 gdk_pixbuf-2.0 gio-2.0 glib-2.0 gmodule-2.0 gobject-2.0
WANTLIB += graphite2 gthread-2.0 gtk-3 harfbuzz lzma m pango-1.0
WANTLIB += pangocairo-1.0 pangoft2-1.0 pcre pixman-1 png pthread
WANTLIB += pthread-stubs util xcb xcb-render xcb-shm xml2 z iconv intl

MODULES=	lang/python \
		x11/gnome

BUILD_DEPENDS=	devel/py-gobject3

LIB_DEPENDS=	x11/gtk+3>=3.5.18 \
		devel/libffi

RUN_DEPENDS=	x11/gnome/devhelp \
		devel/py-gobject3

MODGNOME_TOOLS += desktop-file-utils docbook gtk-update-icon-cache
MODGNOME_TOOLS += gobject-introspection yelp

CONFIGURE_STYLE=	gnu

post-install:
	rm ${PREFIX}/lib/glade/modules/*.{a,la}

.include <bsd.port.mk>
