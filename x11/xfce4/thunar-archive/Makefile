# $OpenBSD: Makefile,v 1.23 2016/11/04 10:02:03 landry Exp $

COMMENT =	Thunar archive plugin

XFCE_VERSION =	0.3.1
THUNAR_PLUGIN =	thunar-archive-plugin
REVISION =	3

# GPLv2
PERMIT_PACKAGE_CDROM =	Yes

MODULES =	x11/xfce4

MODXFCE_ICON_CACHE=	Yes

LIB_DEPENDS =	x11/xfce4/thunar

RUN_DEPENDS =	xarchiver-*|file-roller-*|kdeutils-*:x11/xarchiver

WANTLIB += ICE SM X11 Xcomposite Xcursor Xdamage Xext Xfixes Xi
WANTLIB += Xinerama Xrandr Xrender atk-1.0 cairo exo-1 expat ffi
WANTLIB += fontconfig freetype gdk-x11-2.0 gdk_pixbuf-2.0 gio-2.0
WANTLIB += glib-2.0 gmodule-2.0 gobject-2.0 graphite2 gthread-2.0
WANTLIB += gtk-x11-2.0 harfbuzz m pango-1.0
WANTLIB += pangocairo-1.0 pangoft2-1.0 pcre pixman-1 png pthread
WANTLIB += pthread-stubs thunarx-2 xcb xcb-render xcb-shm xfce4util
WANTLIB += z iconv intl

.include <bsd.port.mk>
