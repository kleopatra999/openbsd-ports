# $OpenBSD: Makefile,v 1.37 2016/03/20 16:12:26 naddy Exp $

# This architecture lacks fast mutexes...
NOT_FOR_ARCHS=		mips64 mips64el

COMMENT=		source code search engine
DISTNAME=		gonzui-1.2
REVISION=		26
CATEGORIES=		textproc www

HOMEPAGE=		http://gonzui.sourceforge.net/

# GPL
PERMIT_PACKAGE_CDROM=	Yes
WANTLIB=		m

MODULES=		lang/ruby lang/ocaml
MODRUBY_REV=		1.8

MASTER_SITES=		${MASTER_SITE_SOURCEFORGE:=gonzui/}

BUILD_DEPENDS=		databases/db/v4 \
			databases/ruby-bdb,${MODRUBY_FLAVOR} \
			lang/ruby/1.8,-iconv
RUN_DEPENDS=		archivers/bzip2 \
			archivers/unzip \
			archivers/xz \
			databases/db/v4 \
			databases/ruby-bdb,${MODRUBY_FLAVOR} \
			lang/ruby/1.8,-iconv \
			textproc/p5-PPI

MODRUBY_ADJ_FILES=	gonzui-db \
			gonzui-import \
			gonzui-remove \
			gonzui-search \
			gonzui-server \
			gonzui-update

CONFIGURE_STYLE=	gnu
CONFIGURE_ARGS=		--with-user="_gonzui" \
			--with-group="_gonzui" \
			--with-rundir="/var/run/gonzui" \
			--with-logdir="/var/log"

# Tests want to do cvs checkouts, apt-get, etc.
NO_TEST=		Yes

# XXX: Bad, but saves a metric buttload of patches.
pre-configure:
	ln -sf ${RUBY} ${WRKDIR}/bin/ruby

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/gonzui/
	${INSTALL_DATA} ${WRKSRC}/gonzuirc.sample \
		${PREFIX}/share/examples/gonzui/

.include <bsd.port.mk>
