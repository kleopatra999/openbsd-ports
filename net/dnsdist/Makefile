# $OpenBSD$

COMMENT=		highly DNS-, DoS- and abuse-aware loadbalancer

V=			1.1.0
DISTNAME=		dnsdist-${V}
EXTRACT_SUFX =		.tar.bz2
PKGNAME=		dnsdist-${V}
CATEGORIES=		net
HOMEPAGE=		http://dnsdist.org/
MAINTAINER=		Peter van Dijk <peter.van.dijk@powerdns.com>

# GPLv2
PERMIT_PACKAGE_CDROM=	Yes

MODULES +=	gcc4 \
		lang/lua
MODGCC4_ARCHS =	*
MODGCC4_LANGS =	c++

CONFIGURE_STYLE=	gnu
CONFIGURE_ARGS+=	--disable-shared \
			--disable-hardening \
			--with-lua \
			LIBEDIT_LIBS='-ledit -lcurses' \
			LIBEDIT_CFLAGS=' '

WANTLIB += m pthread c curses edit ${MODLUA_WANTLIB}
LIB_DEPENDS+=		${MODLUA_LIB_DEPENDS}

BUILD_DEPENDS=		devel/boost

MASTER_SITES=		https://downloads.powerdns.com/releases/

NO_TEST=		Yes

SYSCONFDIR=		${BASESYSCONFDIR}/dnsdist

CONFIGURE_ENV+=		CPPFLAGS="-I${LOCALBASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib"
LIBTOOL_FLAGS=		--tag=disable-static

SEPARATE_BUILD=		No

.include <bsd.port.mk>
