# $OpenBSD: Makefile,v 1.17 2015/01/21 06:13:48 bentley Exp $

COMMENT=	graphic counter language compiler/interpreter

DISTNAME=	gracula-3.0
CATEGORIES=	graphics
REVISION =	0

MASTER_SITES=	${HOMEPAGE}

HOMEPAGE=	http://www.whizkidtech.redprince.net/gcl/

PERMIT_PACKAGE_CDROM=	Yes
WANTLIB=		c m

NO_TEST=	Yes

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/gracula ${PREFIX}/bin
	$(INSTALL_PROGRAM) ${WRKSRC}/sec2000 ${PREFIX}/bin

.include <bsd.port.mk>
