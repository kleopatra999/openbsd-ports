# $OpenBSD: Makefile,v 1.34 2016/10/31 11:31:28 ajacoutot Exp $

COMMENT=		clock application for GNOME

GNOME_PROJECT=		gnome-clocks
GNOME_VERSION=		3.22.1

# GPLv2
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB += ICE SM X11 Xcomposite Xcursor Xdamage Xext Xfixes Xi
WANTLIB += Xinerama Xrandr Xrender atk-1.0 atk-bridge-2.0 atspi
WANTLIB += c cairo cairo-gobject canberra dbus-1 epoxy expat ffi
WANTLIB += fontconfig freetype gdk-3 gdk_pixbuf-2.0 geoclue-2
WANTLIB += geocode-glib gio-2.0 glib-2.0 gmodule-2.0 gnome-desktop-3
WANTLIB += gobject-2.0 graphite2 gsound gthread-2.0 gtk-3 gweather-3
WANTLIB += harfbuzz iconv intl json-glib-1.0 ltdl lzma m ogg pango-1.0
WANTLIB += pangocairo-1.0 pangoft2-1.0 pcre pixman-1 png pthread
WANTLIB += pthread-stubs soup-2.4 sqlite3 vorbis vorbisfile xcb
WANTLIB += xcb-render xcb-shm xml2 z

MODULES=		devel/dconf \
			x11/gnome

LIB_DEPENDS=		audio/gsound \
			geo/geocode-glib \
			x11/gnome/desktop \
			x11/gnome/libgweather

# geocoding.c
BUILD_DEPENDS +=	geo/geoclue2
RUN_DEPENDS +=		geo/geoclue2

MODGNOME_TOOLS=		desktop-file-utils gtk-update-icon-cache yelp

pre-configure:
	sed -i 's,.-Wno-unused-but-set-variable,,' \
		${WRKSRC}/Makefile.in

.include <bsd.port.mk>
