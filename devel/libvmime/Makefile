# $OpenBSD: Makefile,v 1.26 2016/07/09 08:57:11 sthen Exp $

COMMENT=	C++ class library for working with Internet mail

VMIME_V=	0.9.2
DISTNAME=	libvmime-${VMIME_V}+svn603
EXTRACT_SUFX=	.tar.bz2

PKGNAME=	libvmime-${VMIME_V}
REVISION=	7

SHARED_LIBS+=  vmime    2.0     # 0.0

### needed for mail/zarafa (FLAVOR is possible if needed in the future)
#MASTER_SITES=	${MASTER_SITE_SOURCEFORGE:=vmime/}
MASTER_SITES_ZARAFA=http://download.zarafa.com/community/final/7.1/7.1.7-42779/sourcecode/
MASTER_SITES=	${MASTER_SITES_ZARAFA}
MASTER_SITES0=	${MASTER_SITES_ZARAFA:=/vmime-patches/}
PATCH_DIST_STRIP= -p1
PATCHFILES= \
	vmime-0.9.2-header-value-on-next-line.diff:0 \
	vmime-0.9.2-phf-stop-on-whitespace.diff:0 \
	vmime-0.9.2-qp-in-buffers.diff:0 \
	vmime-mixed-qp-in-parameter.diff:0
###

CATEGORIES=	devel mail

HOMEPAGE=	http://www.vmime.org/

MAINTAINER=	Robert Nagy <robert@openbsd.org>

# GPLv3
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB += ffi gmp gnutls hogweed idn m nettle p11-kit pthread stdc++
WANTLIB += tasn1 z

MODULES=	devel/gettext

WRKDIST=	${WRKDIR}/libvmime-${VMIME_V}

# our old gcc is <cxx0x; so "-pedantic" warnings are turned into errors
CFLAGS +=	-fpermissive

USE_GMAKE=	Yes

BUILD_DEPENDS=	archivers/bzip2
LIB_DEPENDS=	security/gnutls

CONFIGURE_STYLE=gnu
CONFIGURE_ENV=	CPPFLAGS="-I${LOCALBASE}/include" \
		LDFLAGS="-L${LOCALBASE}/lib" \
		EXTRA_CFLAGS="${CFLAGS}"

# security/libgsasl; not real need for this so far
CONFIGURE_ARGS += --disable-sasl

.include <bsd.port.mk>
