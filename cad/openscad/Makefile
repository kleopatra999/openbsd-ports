# $OpenBSD: Makefile,v 1.14 2016/03/26 20:37:35 zhuk Exp $

COMMENT =		the programmer's solid 3D CAD modeller#'
BROKEN-sparc64=	SIGILL on src/cgalutils.cc with CGAL-4.6.3

V =			2015.03-2
DISTNAME =		openscad-${V:S/-/./}

CATEGORIES =		cad

HOMEPAGE =		http://www.openscad.org/

# GPLv2+ with CGAL exception
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB += CGAL GL GLEW GLU ICE SM X11 Xext Xi Xinerama Xrender
WANTLIB += boost_filesystem-mt boost_program_options-mt boost_regex-mt
WANTLIB += boost_system-mt boost_thread-mt c fontconfig freetype
WANTLIB += glib-2.0 gmp harfbuzz m mpfr opencsg pthread qscintilla2
WANTLIB += stdc++ z lib/qt4/QtGui lib/qt4/QtOpenGL

MASTER_SITES =		http://files.openscad.org/
DISTFILES =		openscad-${V}.src.tar.gz

MODULES =		devel/gettext \
			devel/qmake \
			x11/qt4
BUILD_DEPENDS =		devel/bison \
			math/eigen3
LIB_DEPENDS =		devel/boost \
			devel/gmp \
			devel/harfbuzz \
			devel/mpfr \
			editors/qscintilla \
			graphics/glew \
			graphics/opencsg \
			math/cgal

RUN_DEPENDS =		devel/desktop-file-utils \
			fonts/liberation-fonts

MODQMAKE_ARGS =		VERSION=${V}
SEPARATE_BUILD =	No

NO_TEST =		Yes

WRKDIST =		${WRKDIR}/openscad-$V

pre-configure:
	ln -sf ${LOCALBASE}/bin/bison ${WRKDIR}/bin/yacc

.include <bsd.port.mk>
