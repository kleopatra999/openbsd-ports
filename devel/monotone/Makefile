# $OpenBSD: Makefile,v 1.10 2016/09/23 09:16:54 sthen Exp $

COMMENT=	distributed version control system

VERSION=	1.1
DISTNAME=	monotone-${VERSION}
CATEGORIES=	devel
REVISION=	0

HOMEPAGE=	http://monotone.ca/

# GPLv2
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB += botan-1.10 c idn m pcre pthread sqlite3 stdc++ z
WANTLIB += ${MODLUA_WANTLIB}

MASTER_SITES=	${HOMEPAGE}/downloads/${VERSION}/
EXTRACT_SUFX=	.tar.bz2

MODULES=	devel/gettext \
		lang/lua
BUILD_DEPENDS=	devel/boost
LIB_DEPENDS=	databases/sqlite3 \
		devel/libidn \
		devel/pcre \
		security/botan

USE_GMAKE=	Yes
CONFIGURE_STYLE=gnu
CONFIGURE_ENV=	LDFLAGS="-L${LOCALBASE}/lib" \
		CPPFLAGS="${CFLAGS} -I${LOCALBASE}/include" \
		CFLAGS="${CFLAGS} -I${LOCALBASE}/include"
TEST_FLAGS=	HOME=${WRKSRC}
FAKE_FLAGS=	sysconfdir=${PREFIX}/share/examples/monotone/

.include <bsd.port.mk>
