# $OpenBSD: Makefile,v 1.25 2016/08/29 09:13:37 jca Exp $

COMMENT=		small tool to make annotations on the screen

DISTNAME=		gromit-20041213
REVISION=		13
CATEGORIES=		x11

HOMEPAGE=		http://www.home.unix-ag.org/simon/gromit/

MAINTAINER=		Michael Knudsen <mk@molioner.dk>

# GPL
PERMIT_PACKAGE_CDROM=	Yes

MASTER_SITES=		${HOMEPAGE}

LIB_DEPENDS=		x11/gtk+2

WANTLIB += X11 Xau Xcomposite Xcursor Xdamage Xdmcp Xext Xfixes
WANTLIB += Xi Xinerama Xrandr Xrender atk-1.0 c cairo expat fontconfig
WANTLIB += freetype gdk-x11-2.0 gdk_pixbuf-2.0 gio-2.0 glib-2.0
WANTLIB += gmodule-2.0 gobject-2.0 graphite2 gtk-x11-2.0 harfbuzz
WANTLIB += intl m pango-1.0 pangocairo-1.0 pangoft2-1.0 pcre pixman-1
WANTLIB += png pthread pthread-stubs xcb xcb-render xcb-shm z

NO_TEST=		Yes

DOCDIR=			${PREFIX}/share/doc/gromit/

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/gromit ${PREFIX}/bin
	${INSTALL_DATA_DIR} ${DOCDIR}
	${INSTALL_DATA} ${WRKSRC}/README ${DOCDIR}
	${INSTALL_DATA} ${WRKSRC}/gromitrc_gsr ${DOCDIR}gromitrc

.include <bsd.port.mk>
