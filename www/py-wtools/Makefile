# $OpenBSD: Makefile,v 1.7 2017/01/03 19:28:49 landry Exp $

COMMENT=		WSDL parsing services package for Python

MODPY_EGG_VERSION=	0.4.4
DISTNAME=		wstools-${MODPY_EGG_VERSION}
PKGNAME=		py-${DISTNAME}
CATEGORIES=		www
REVISION=		0

# BSD
PERMIT_PACKAGE_CDROM=	Yes

MODULES=		lang/python

MODPY_PI =		Yes
MODPY_SETUPTOOLS=	Yes

FLAVORS =		python3
FLAVOR ?=

BUILD_DEPENDS=		devel/py-six${MODPY_FLAVOR}
RUN_DEPENDS =		devel/py-six${MODPY_FLAVOR}

# Tests are not provided in pypi tarball
NO_TEST=		Yes

.include <bsd.port.mk>
