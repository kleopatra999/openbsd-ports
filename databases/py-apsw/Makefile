# $OpenBSD: Makefile,v 1.8 2017/01/03 19:17:24 landry Exp $

COMMENT =	thin SQLite wrapper for Python

MODPY_EGG_VERSION = 3.8.0.2
REVISION =	3
DISTNAME =	apsw-${MODPY_EGG_VERSION}-r1
EXTRACT_SUFX =	.zip
PKGNAME =	py-apsw-${MODPY_EGG_VERSION}
CATEGORIES =	databases

HOMEPAGE=	https://rogerbinns.github.io/apsw/
MASTER_SITES=	${MASTER_SITE_GOOGLECODE:=apsw/}
PORTROACH=	site:https://github.com/rogerbinns/apsw/releases

# zlib
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB += ${MODPY_WANTLIB} pthread sqlite3

LIB_DEPENDS =	databases/sqlite3

MODULES =	lang/python

FLAVORS =	python3
FLAVOR ?=

MODPY_DISTUTILS_BUILDARGS = build_ext -I${LOCALBASE}/include

do-test: fake
	@cd ${WRKSRC} && ${SETENV} PYTHONPATH=${WRKINST}${MODPY_SITEPKG} \
		${MODPY_BIN} ./tests.py

.include <bsd.port.mk>
