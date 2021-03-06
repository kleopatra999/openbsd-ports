# $OpenBSD: Makefile,v 1.60 2017/01/03 19:21:18 landry Exp $

COMMENT=	Python charting and plotting API

MODPY_EGG_VERSION =	1.5.3
DISTNAME =		matplotlib-${MODPY_EGG_VERSION}
PKGNAME =		py-${DISTNAME}
REVISION =		1
CATEGORIES =		graphics devel math

HOMEPAGE=	http://matplotlib.sourceforge.net/

MAINTAINER =	Daniel Dickman <daniel@openbsd.org>

# BSD-like
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB += ${MODPY_WANTLIB}
WANTLIB += freetype m png stdc++ z

MODULES=	lang/python

FLAVORS=	python3
FLAVOR?=

MODPY_PI =		Yes
MODPY_SETUPTOOLS =	Yes

COMMON_DEPENDS=	devel/py-tz${MODPY_FLAVOR} \
		devel/py-dateutil${MODPY_FLAVOR} \
		devel/py-parsing${MODPY_FLAVOR} \
		devel/py-six${MODPY_FLAVOR} \
		math/py-numpy${MODPY_FLAVOR} \
		graphics/py-Pillow${MODPY_FLAVOR} \
		graphics/py-cycler${MODPY_FLAVOR} \
		${MODPY_TKINTER_DEPENDS}

BUILD_DEPENDS=	${COMMON_DEPENDS}
RUN_DEPENDS=	${COMMON_DEPENDS}

.if ${FLAVOR:Mpython3}
COMMON_DEPENDS +=	devel/py-gobject3${MODPY_FLAVOR}
# pygobject GTK3 introspection (not provided by indirect dependencies)
COMMON_DEPENDS +=	x11/gtk+3
.else
COMMON_DEPENDS +=	x11/py-gtk2
.endif

LIB_DEPENDS=	graphics/png
TEST_DEPENDS =	${RUN_DEPENDS} \
		devel/py-nose${MODPY_FLAVOR}

MAKE_ENV+=	LDSHARED="${CC} -shared -fPIC"

EXAMPLESDIR=	${PREFIX}/share/examples/${MODPY_PY_PREFIX}matplotlib

pre-configure:
	@find ${WRKSRC}/examples -name \*.py | xargs ${MODPY_BIN_ADJ}
	${SUBST_CMD} ${WRKSRC}/setupext.py
	${SUBST_CMD} ${WRKSRC}/lib/matplotlib/sphinxext/tests/test_tinypages.py

post-install:
	${INSTALL_DATA_DIR} ${EXAMPLESDIR}
	cd ${WRKSRC}/examples && pax -rw * ${EXAMPLESDIR}

# http://matplotlib.org/devel/testing.html
do-test: fake
	cd ${WRKSRC} && ${MAKE_ENV} PYTHONPATH=${WRKINST}${MODPY_SITEPKG} \
		${MODPY_BIN} -c 'import matplotlib ; matplotlib.test()'

.include <bsd.port.mk>
