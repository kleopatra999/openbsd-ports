# $OpenBSD: Makefile,v 1.3 2017/01/08 11:51:14 sthen Exp $

DISTNAME =		qtbase-opensource-src-${DIST_VERSION}
QT5NAME =		Qt5 core

COMMENT-main =		C++ general-purpose toolkit
COMMENT-global =	global Qt5 documentation internals
COMMENT-mysql =		MySQL plugin for Qt5
COMMENT-psql =		PostgresSQL plugin for Qt5
COMMENT-sqlite2 =	SQLite 2.x plugin for Qt5
COMMENT-tds =		TDS plugin for Qt5

PKGNAME-mysql =		qt5-mysql-${VERSION}
PKGNAME-global = 	qt5-global-${VERSION}
PKGNAME-psql =		qt5-postgresql-${VERSION}
PKGNAME-sqlite2 =	qt5-sqlite2-${VERSION}
PKGNAME-tds =		qt5-tds-${VERSION}

REVISION-main =		1

PKG_ARCH-global =	*
PKG_ARCH-examples =	*

DPB_PROPERTIES =	parallel

SHARED_LIBS +=	Qt5Concurrent		2.0
SHARED_LIBS +=	Qt5Core			2.0
SHARED_LIBS +=	Qt5DBus			2.0
SHARED_LIBS +=	Qt5Gui			2.0
SHARED_LIBS +=	Qt5Network		2.0
SHARED_LIBS +=	Qt5OpenGL		2.0
SHARED_LIBS +=	Qt5PrintSupport		2.0
SHARED_LIBS +=	Qt5Sql			2.0
SHARED_LIBS +=	Qt5Test			2.0
SHARED_LIBS +=	Qt5Widgets		2.0
SHARED_LIBS +=	Qt5Xml			2.0
SHARED_LIBS +=	Qt5EglDeviceIntegration	1.0
SHARED_LIBS +=	Qt5XcbQpa		1.0

WANTLIB-main =  ${WANTLIB}
WANTLIB-main += EGL GL ICE SM X11 X11-xcb Xcomposite Xcursor Xdamage
WANTLIB-main += Xext Xfixes Xi Xinerama Xrandr Xrender atk-1.0 c cairo
WANTLIB-main += cups dbus-1 execinfo fontconfig freetype gdk-x11-2.0
WANTLIB-main += gdk_pixbuf-2.0 gio-2.0 glib-2.0 gobject-2.0 gthread-2.0
WANTLIB-main += gtk-x11-2.0 harfbuzz icudata icui18n icuuc iodbc jpeg
WANTLIB-main += m pango-1.0 pangocairo-1.0 pangoft2-1.0 pcre16 png
WANTLIB-main += proxy pthread sqlite3 xcb xcb-glx xcb-icccm xcb-image
WANTLIB-main += xcb-keysyms xcb-randr xcb-render xcb-render-util xcb-shape
WANTLIB-main += xcb-shm xcb-sync xcb-xfixes xcb-xinerama xcb-xkb xkbcommon
WANTLIB-main += xkbcommon-x11 z
WANTLIB-main += drm gbm

WANTLIB-global =

WANTLIB-mysql =		${MODGCC4_CPPWANTLIB} Qt5Core Qt5Sql
WANTLIB-mysql +=	crypto m pthread mysqlclient_r ssl z

WANTLIB-psql =		${MODGCC4_CPPWANTLIB} Qt5Core Qt5Sql
WANTLIB-psql +=		m pthread pq

WANTLIB-sqlite2 =	${MODGCC4_CPPWANTLIB} Qt5Core Qt5Sql
WANTLIB-sqlite2 +=	m pthread sqlite

WANTLIB-tds =		${MODGCC4_CPPWANTLIB} Qt5Core Qt5Sql
WANTLIB-tds +=		m pthread sybdb

# there is no -sqlite3 because it's heavily used by Qt itself (.qch files)
MULTI_PACKAGES =	-main -examples -global -mysql -psql -sqlite2 -tds

MODULES =		devel/gettext

# qmake module is used only for running tests and setting vars
MODQT_DEPS =		No
MODQMAKE_PROJECTS =	tests/tests.pro

# no leveldb dependency, requires -lmemenv; QtWebKit uses internal version
LIB_DEPENDS-main =	${LIB_DEPENDS} \
			databases/iodbc \
			databases/sqlite3 \
			devel/atk \
			devel/harfbuzz \
			devel/libexecinfo \
			devel/pango \
			graphics/cairo \
			graphics/gdk-pixbuf2 \
			net/libproxy \
			print/cups,-libs \
			textproc/icu4c \
			x11/gtk+2 \
			x11/xkbcommon

LIB_DEPENDS-global =

LIB_DEPENDS-mysql =	${BASE_PKGPATH},-main>=${VERSION:R},<${QT5_NEXT_VERSION} \
			${MODGCC4_CPPLIBDEP} \
			databases/mariadb

LIB_DEPENDS-psql =	${BASE_PKGPATH},-main>=${VERSION:R},<${QT5_NEXT_VERSION} \
			${MODGCC4_CPPLIBDEP} \
			databases/postgresql

LIB_DEPENDS-sqlite2 =	${BASE_PKGPATH},-main>=${VERSION:R},<${QT5_NEXT_VERSION} \
			${MODGCC4_CPPLIBDEP} \
			databases/sqlite

LIB_DEPENDS-tds =	${BASE_PKGPATH},-main>=${VERSION:R},<${QT5_NEXT_VERSION} \
			${MODGCC4_CPPLIBDEP} \
			databases/freetds

# nothing in qtbase links to pulseaudio, but configure checks
# are recorded
BUILD_DEPENDS =		audio/pulseaudio \
			geo/geoclue \
			x11/dbus

RUN_DEPENDS-main =	${RUN_DEPENDS} \
			geo/geoclue \
			x11/dbus
RUN_DEPENDS-global =
RUN_DEPENDS-examples =
RUN_DEPENDS-mysql =
RUN_DEPENDS-psql =
RUN_DEPENDS-sqlite2 =
RUN_DEPENDS-tds =

CONFIGURE_STYLE =	simple

FLAVORS =		debug
PSEUDO_FLAVORS =	no_examples
FLAVOR ?=

# readability macros
QT_BASEDIR =	${PREFIX}/lib/qt5
QT_INCDIR =	${PREFIX}/include/X11/qt5
QT_EXAMPLES =	${QT_BASEDIR}/examples
QT_DOC =	${PREFIX}/share/doc/qt5
QT_PLUGINSDIR =	${QT_BASEDIR}/plugins
QT_BINDIR =	${QT_BASEDIR}/bin
QT_PKGCFGDIR =	${QT_BASEDIR}/pkgconfig
QT_CMAKEDIR =	${QT_BASEDIR}/cmake

# generic args
CONFIGURE_ARGS =	-confirm-license \
			-opensource \
			-rpath \
			-shared \
			-verbose \
			-no-pch \
			-no-compile-examples

# Don't run tests inside main build.
# XXX It looks like affecting other Qt modules as well.
CONFIGURE_ARGS +=	-nomake tests

.if ${FLAVOR:Mdebug}
CONFIGURE_ARGS +=	-debug
.else
CONFIGURE_ARGS +=	-release
.endif

# paths
CONFIGURE_ARGS +=	-sysconfdir ${SYSCONFDIR} \
			-prefix ${QT_BASEDIR} \
			-plugindir ${QT_PLUGINSDIR} \
			-libdir ${QT_BASEDIR} \
			-headerdir ${QT_INCDIR} \
			-examplesdir ${QT_EXAMPLES} \
			-docdir ${QT_DOC} \
			-datadir ${QT_BASEDIR} \
			-bindir ${QT_BINDIR} \
			-R${X11BASE}/lib \
			-L${X11BASE}/lib

# other options
CONFIGURE_ARGS +=	-c++11 \
			-no-alsa \
			-no-journald \
			-no-mtdev \
			-opengl desktop \
			-system-harfbuzz \
			-system-proxies \
			-system-sqlite \
			-system-xcb

.if ${MACHINE_ARCH} == "amd64" || ${MACHINE_ARCH} == "i386"
# AVX:    Sandy Bridge/Haswell, but not all models. AMD Bulldozer/Jaguar.
# SSE4.2: Nehalem, Silvermont Atom, AMD Bulldozer/Jaguar.
# SSE4.1: Core 2 (Penryn), Nehalem, Silvermont Atom, AMD Bulldozer/Jaguar.
# SSSE3:  Core 2 Duo, Atom, AMD Bulldozer/Bobcat.
# SSE3:   missing on very early 64-bit AMD.
CONFIGURE_ARGS +=	-no-sse4.1 -no-sse4.2 -no-avx -no-avx2
CONFIGURE_ARGS +=	-no-ssse3 -no-sse3
.endif

.if ${MACHINE_ARCH} == "i386"
CONFIGURE_ARGS +=	-no-sse2
.endif

CONFIGURE_ENV +=	${MODQMAKE_ENV}
MAKE_ENV +=		${MODQMAKE_ENV}

.include <bsd.port.arch.mk>

# See qtbase/tests/README for details
TEST_IS_INTERACTIVE =	X11
TEST_DEPENDS =		audio/sox
#			kde4-minimal-*|kdebase-*:meta/kde4,-minimal

pre-configure:
	@gccbasedir=`ecpp -print-search-dirs | awk '/^install:/{print $$2}'`; \
	perl ${PORTSDIR}/infrastructure/bin/pkg_subst \
	    -D OPENBSD_INCDIR_PREPEND="$${gccbasedir}include" \
	    ${WRKSRC}/mkspecs/openbsd-g++/qmake.conf

do-test:
	#
	# WARNING!
	# Many tests won't run if window manager has either
	# "focus follows pointer", or "click to activate" policy.
	#
	${MODQMAKE_configure}
	${MODQMAKE_build}

post-install:
	# often-used includes directory
	! test -d ${PREFIX}/lib/qt5 || \
	    cd ${PREFIX}/lib/qt5 && ln -sf ../../include/X11/qt5 include

.include <bsd.port.mk>
