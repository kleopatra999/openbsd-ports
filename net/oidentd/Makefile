# $OpenBSD: Makefile,v 1.24 2016/12/23 11:28:27 jca Exp $

COMMENT=	ident daemon with custom responses and NAT support
DISTNAME=	oidentd-2.0.8
CATEGORIES=	net
MASTER_SITES=	${MASTER_SITE_SOURCEFORGE:=ojnk/}

HOMEPAGE=	http://ojnk.sourceforge.net/

# GPLv2 only
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB=		c

CONFIGURE_STYLE=gnu

pre-configure:
	sed -i 's,/etc,${SYSCONFDIR},g' \
		${WRKSRC}/doc/oidentd_masq.conf.5 ${WRKSRC}/doc/oidentd.8 \
		${WRKSRC}/doc/oidentd.conf.5 ${WRKSRC}/src/oidentd_options.c \
		${WRKSRC}/src/oidentd.h

.include <bsd.port.mk>
