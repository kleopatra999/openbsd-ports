# $OpenBSD: Makefile,v 1.9 2016/01/04 12:32:27 ajacoutot Exp $

COMMENT=	OCR program for pnm files

DISTNAME=	ocrad-0.25
CATEGORIES=	graphics
EXTRACT_SUFX=	.tar.lz

MAINTAINER=	William Yodlowsky <william@openbsd.org>

# GPLv3
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB=	c m stdc++

MASTER_SITES=	${MASTER_SITE_GNU:=ocrad/}

CONFIGURE_STYLE=gnu

MAKE_FLAGS=	CXX="${CXX}" CXXFLAGS="${CXXFLAGS}"

post-install:
	${INSTALL_MAN} ${WRKBUILD}/doc/ocrad.1 ${PREFIX}/man/man1
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/ocrad
	${INSTALL_DATA} ${WRKSRC}/README ${PREFIX}/share/doc/ocrad
	rm ${PREFIX}/include/ocradlib.h ${PREFIX}/lib/libocrad.a

.include <bsd.port.mk>
