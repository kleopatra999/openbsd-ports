# $OpenBSD: Makefile,v 1.28 2016/03/11 20:28:22 naddy Exp $

COMMENT=	patent-free speech codec

DISTNAME=	speex-1.2rc1
REVISION=	1
CATEGORIES=	audio
HOMEPAGE=	http://www.speex.org/
SHARED_LIBS +=	speex                8.0      # .6.0
SHARED_LIBS +=	speexdsp             1.0      # .6.0

MAINTAINER=	Christian Weisgerber <naddy@openbsd.org>

# BSD
PERMIT_PACKAGE_CDROM=	Yes

MASTER_SITES=	http://downloads.xiph.org/releases/speex/

LIB_DEPENDS=	audio/libogg
WANTLIB=	c m ogg>=5 sndio

CONFIGURE_STYLE=gnu
CONFIGURE_ARGS=	--with-ogg=${LOCALBASE}
CONFIGURE_ENV=	CPPFLAGS="-DUSE_SNDIO"

MAKE_FLAGS=	docdir=${TRUEPREFIX}/share/doc/speex \
		mandir=${TRUEPREFIX}/man


.include <bsd.port.mk>
