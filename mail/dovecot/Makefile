# $OpenBSD: Makefile,v 1.248 2016/12/04 21:36:02 sthen Exp $

COMMENT-server=	compact IMAP/POP3 server
COMMENT-ldap=	LDAP authentication / dictionary support for Dovecot
COMMENT-mysql=	MySQL authentication / dictionary support for Dovecot
COMMENT-postgresql= PostgreSQL authentication / dictionary support for Dovecot

V_MAJOR=	2.2
V_DOVECOT=	2.2.27

DISTNAME=	dovecot-${V_DOVECOT}
PKGNAME=	dovecot-${V_DOVECOT}
PKGNAME-server=	dovecot-${V_DOVECOT}
PKGSPEC-server=	dovecot-=${V_DOVECOT}
PKGNAME-ldap=	dovecot-ldap-${V_DOVECOT}
PKGNAME-mysql=	dovecot-mysql-${V_DOVECOT}
PKGNAME-postgresql= dovecot-postgresql-${V_DOVECOT}
CATEGORIES=	mail
MASTER_SITES=	${HOMEPAGE}releases/${V_MAJOR}/

SHARED_LIBS=	dovecot-compression 0.0 \
		dovecot-dsync	0.0 \
		dovecot-fts	0.0 \
		dovecot-lda	2.0 \
		dovecot-ldap    0.0 \
		dovecot-login	2.0 \
		dovecot-sql	2.0 \
		dovecot-storage	2.0 \
		dovecot		2.0

HOMEPAGE=	https://dovecot.org/

MAINTAINER=	Brad Smith <brad@comstyle.com>

# LGPLv2.1 and MIT
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB-server=	bz2 c crypto iconv lz4 lzma pthread sqlite3 ssl z
WANTLIB-ldap=	crypto lber-2.4 ldap-2.4 sasl2 ssl lib/dovecot/dovecot
WANTLIB-mysql=	crypto m lib/mysql/mysqlclient pthread ssl stdc++ z
WANTLIB-postgresql= crypto pq>=4 ssl

LIB_DEPENDS+=	archivers/bzip2 \
		archivers/lz4 \
		archivers/xz \
		converters/libiconv \
		databases/sqlite3
LIB_DEPENDS-ldap= ${BASE_PKGPATH}=${V_DOVECOT} \
		databases/openldap
LIB_DEPENDS-mysql= databases/mariadb
RUN_DEPENDS-mysql= ${BASE_PKGPATH}=${V_DOVECOT}
LIB_DEPENDS-postgresql= databases/postgresql
RUN_DEPENDS-postgresql= ${BASE_PKGPATH}=${V_DOVECOT}

CONFIGURE_STYLE= gnu
CONFIGURE_ARGS=	--with-rundir=/var/dovecot \
		--with-sql=plugin \
		--with-sqlite \
		--with-statedir=/var/dovecot \
		--without-icu \
		--without-nss \
		--without-pam \
		--without-shadow \
		--without-stemmer \
		--without-textcat \
		--without-vpopmail
CONFIGURE_ENV=	CPPFLAGS="-I${LOCALBASE}/include" \
		LDFLAGS="-L${LOCALBASE}/lib"

PSEUDO_FLAVORS=	no_db no_ldap no_mysql no_postgresql
FLAVOR?=
.if ${FLAVOR:Mno_db}
FLAVOR+=	no_ldap no_mysql no_postgresql
.endif

MULTI_PACKAGES= -server -ldap -mysql -postgresql
SUBPACKAGE?=	-server

.include <bsd.port.arch.mk>

.if ${BUILD_PACKAGES:M-ldap}
CONFIGURE_ARGS+=--with-ldap=plugin
.endif

.if ${BUILD_PACKAGES:M-mysql}
CONFIGURE_ARGS+=--with-mysql
.endif

.if ${BUILD_PACKAGES:M-postgresql}
CONFIGURE_ARGS+=--with-pgsql
.endif

pre-build:
	@${SUBST_CMD} ${WRKSRC}/doc/example-config/conf.d/10-mail.conf

post-install:
	${INSTALL_DATA} ${WRKSRC}/doc/dovecot-openssl.cnf \
		${PREFIX}/share/examples/dovecot
	${INSTALL_SCRIPT} ${WRKSRC}/doc/mkcert.sh \
		${PREFIX}/sbin/dovecot-mkcert.sh
	@rm ${PREFIX}/share/doc/dovecot/{dovecot-openssl.cnf,mkcert.sh}
	@find ${PREFIX}/lib/dovecot -name '*.a' -print | xargs rm
	@find ${PREFIX}/lib/dovecot -name '*.la' -print | xargs rm

.include <bsd.port.mk>
