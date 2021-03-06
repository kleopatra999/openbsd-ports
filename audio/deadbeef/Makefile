# $OpenBSD: Makefile,v 1.29 2016/11/04 11:35:18 sthen Exp $

COMMENT =		DeaDBeeF is an audio player
DISTNAME =		deadbeef-0.7.2
REVISION =		2
CATEGORIES =		audio

HOMEPAGE =		http://deadbeef.sourceforge.net/

# GPLv2 & LGPLv2.1
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB += FLAC ICE Imlib2 SM X11 Xcomposite Xcursor Xdamage Xext Xfixes
WANTLIB += Xi Xinerama Xrandr Xrender atk-1.0 atk-bridge-2.0 atspi
WANTLIB += avcodec avformat avutil c cairo cairo-gobject cddb cdio
WANTLIB += crypto curl dbus-1 epoxy expat faad ffi fontconfig freetype
WANTLIB += gdk-3 gdk_pixbuf-2.0 gio-2.0 glib-2.0 gmodule-2.0 gobject-2.0
WANTLIB += graphite2 gthread-2.0 gtk-3 harfbuzz iconv intl jansson m mad
WANTLIB += mms mp4ff mpcdec nghttp2 ogg pango-1.0 pangocairo-1.0
WANTLIB += pangoft2-1.0 pcre pixman-1 png pthread pthread-stubs sndfile
WANTLIB += sndio ssl vorbis vorbisenc vorbisfile wavpack xcb xcb-render
WANTLIB += xcb-shm z zip

MASTER_SITES =		${MASTER_SITE_SOURCEFORGE:=deadbeef/}
EXTRACT_SUFX =		.tar.bz2

MODULES =		textproc/intltool

BUILD_DEPENDS =		${MODGNU_AUTOCONF_DEPENDS} \
			${MODGNU_AUTOMAKE_DEPENDS}

.if ${MACHINE_ARCH} == "amd64" || ${MACHINE_ARCH} == "i386"
BUILD_DEPENDS +=	devel/yasm
.endif

RUN_DEPENDS =		devel/desktop-file-utils \
			x11/gtk+3,-guic

LIB_DEPENDS =		archivers/libzip \
			audio/faad \
			audio/flac \
			audio/libcdio \
			audio/libmad \
			audio/libogg \
			audio/libsndfile \
			audio/libvorbis \
			audio/musepack \
			audio/wavpack \
			devel/jansson \
			graphics/ffmpeg \
			graphics/imlib2 \
			multimedia/libmms \
			net/curl \
			x11/dbus \
			x11/gtk+3

USE_GMAKE =		Yes
USE_LIBTOOL =		gnu
LIBTOOL_FLAGS =		--tag=disable-static

NO_TEST =		Yes

AUTOCONF_VERSION =	2.69
AUTOMAKE_VERSION =	1.11

CONFIGURE_STYLE =	gnu
CONFIGURE_ARGS +=	--disable-static \
			--disable-abstract-socket \
			--disable-adplug \
			--disable-alsa \
			--disable-coreaudio \
			--disable-gme \
			--disable-gtk2 \
			--disable-libmpg123 \
			--disable-mono2stereo \
			--disable-oss \
			--disable-pulse \
			--disable-sid \
			--disable-src \
			--disable-supereq \
			--disable-wildmidi \
			--disable-wma
CONFIGURE_ENV +=	CPPFLAGS='-I${LOCALBASE}/lib/libzip/include \
				  -I${X11BASE}/include \
				  -I${WRKSRC}/plugins/dumb/dumb-kode54/include' \
			LDFLAGS='-L${LOCALBASE}/lib -L${X11BASE}/lib'

post-patch:
	@mkdir -p ${WRKSRC}/m4 # XXX need for autoreconf
	@mkdir -p ${WRKSRC}/plugins/sndio
	@cp ${FILESDIR}/{Makefile.am,sndio.c} ${WRKSRC}/plugins/sndio

pre-configure:
	@cd ${WRKSRC}; env AUTOCONF_VERSION=${AUTOCONF_VERSION} \
		AUTOMAKE_VERSION=${AUTOMAKE_VERSION} autoreconf

post-install:
	@rm ${PREFIX}/lib/deadbeef/*.la

.include <bsd.port.mk>
