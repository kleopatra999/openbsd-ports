# $OpenBSD: Makefile,v 1.33 2016/09/13 11:44:07 naddy Exp $

COMMENT =	gateway to send and receive SMS through GSM mobile phones

DISTNAME =	smstools3-3.1.15
REVISION =	1

CATEGORIES =	comms

HOMEPAGE =	http://smstools3.kekekasvi.com/

MAINTAINER =	Stuart Henderson <sthen@openbsd.org>

# GPLv2
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB =	c iconv mm

MASTER_SITES =	${HOMEPAGE}/packages/

# some scripts use formail
RUN_DEPENDS =	mail/procmail
LIB_DEPENDS =	converters/libiconv \
		devel/mm

USE_GMAKE =	Yes
NO_TEST =	Yes
WRKDIST =	${WRKDIR}/smstools3
WRKSRC =	${WRKDIST}/src

EXTRA_CFLAGS +=	-I${LOCALBASE}/include -L${LOCALBASE}/lib

MAKE_FLAGS +=	CFLAGS="${CFLAGS} -D NUMBER_OF_MODEMS=64 `mm-config --cflags`"

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/smsd ${PREFIX}/bin
	${INSTALL_SCRIPT} ${WRKDIST}/scripts/{sendsms,sms2html} \
		${WRKDIST}/scripts/{sms2unicode,unicode2sms} \
		${PREFIX}/bin
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/smstools \
		${PREFIX}/share/examples/smstools/scripts
	${INSTALL_DATA} ${WRKDIST}/examples/* \
		${PREFIX}/share/examples/smstools
	${INSTALL_DATA} ${WRKDIST}/scripts/* \
		${PREFIX}/share/examples/smstools/scripts
	rm ${PREFIX}/share/examples/smstools/scripts/*.orig
	${SUBST_DATA} ${FILESDIR}/smsd.conf.openbsd \
		${PREFIX}/share/examples/smstools/smsd.conf.openbsd
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/smstools
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/smstools/slideshow
	${INSTALL_DATA} ${WRKDIST}/doc/*html ${PREFIX}/share/doc/smstools
	${INSTALL_DATA} ${WRKDIST}/doc/slideshow/* \
		${PREFIX}/share/doc/smstools/slideshow

.include <bsd.port.mk>
