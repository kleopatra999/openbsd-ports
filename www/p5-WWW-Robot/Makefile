# $OpenBSD: Makefile,v 1.9 2016/03/20 19:57:23 naddy Exp $

COMMENT=		configurable web traversal engine

DISTNAME=		WWW-Robot-0.026
CATEGORIES=		www

# perl
PERMIT_PACKAGE_CDROM=	Yes

MODULES=		cpan
PKG_ARCH=		*

BUILD_DEPENDS=		${RUN_DEPENDS}
RUN_DEPENDS=		www/p5-HTML-Parser \
			www/p5-HTML-Tree \
			www/p5-URI \
			www/p5-libwww 

MODCPAN_EXAMPLES=	Yes

.include <bsd.port.mk>
