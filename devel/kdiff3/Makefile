# $OpenBSD: Makefile,v 1.9 2016/04/07 02:32:02 lteo Exp $

COMMENT =	compares and merges multiple files or directories

DISTNAME =	kdiff3-0.9.98
REVISION =	0
CATEGORIES =	devel x11/kde
HOMEPAGE =	http://kdiff3.sourceforge.net/

MASTER_SITES =	${MASTER_SITE_SOURCEFORGE:=kdiff3/}

# GPLv2
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB =	ICE QtGui SM X11 Xext Xi Xinerama Xrender
WANTLIB +=	c fontconfig freetype m pthread stdc++

MODULES =	x11/qt4 devel/qmake

CONFIGURE_STYLE =	qmake
MODQMAKE_PROJECTS =	src-QT4/kdiff3.pro

pre-configure:
	@${SUBST_CMD} ${WRKSRC}/src-QT4/kdiff3.pro

.include <bsd.port.mk>
