# $OpenBSD: Makefile,v 1.35 2016/12/20 18:49:17 jasper Exp $

COMMENT=		distributed RESTful search and analytics

V=			5.1.1
DISTNAME=		elasticsearch-$V
REVISION=		0
CATEGORIES=		textproc

HOMEPAGE=		https://www.elastic.co/products/elasticsearch

MAINTAINER=		Jasper Lievisse Adriaanse <jasper@openbsd.org>

# Apache2
PERMIT_PACKAGE_CDROM=	Yes

MASTER_SITES=		https://artifacts.elastic.co/downloads/elasticsearch/

MODULES=		java
MODJAVA_VER=		1.8+
MODJAVA_JRERUN=		Yes

RUN_DEPENDS=		java/javaPathHelper \
			shells/bash

NO_BUILD=		Yes
NO_TEST=		Yes

ES_BASE=		${PREFIX}/elasticsearch/

do-install:
	cd ${WRKSRC}/bin; \
		sed -i 's,#!/bin/bash,#!${LOCALBASE}/bin/bash,' \
		elasticsearch elasticsearch{-plugin,-translog,.in.sh}
	${INSTALL_DATA_DIR} ${ES_BASE}/{bin,lib,modules,plugins}/ \
		${PREFIX}/share/{doc,examples}/elasticsearch/
.for b in elasticsearch elasticsearch-plugin elasticsearch-translog
	${INSTALL_SCRIPT} ${WRKSRC}/bin/$b ${ES_BASE}/bin/
.endfor
	${INSTALL_DATA} ${WRKSRC}/lib/*.jar ${ES_BASE}/lib/
.for c in ${WRKSRC}/config/*.yml ${WRKSRC}/config/*.options ${WRKSRC}/config/*.properties ${WRKSRC}/bin/elasticsearch.in.sh
	${INSTALL_DATA} ${WRKSRC}/$c ${PREFIX}/share/examples/elasticsearch/
.endfor
	cp -R ${WRKSRC}/modules ${ES_BASE}
	${INSTALL_DATA} ${WRKSRC}/README.textile ${PREFIX}/share/doc/elasticsearch/

.include <bsd.port.mk>
