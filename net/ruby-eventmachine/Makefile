# $OpenBSD: Makefile,v 1.23 2016/11/04 21:39:12 jeremy Exp $

COMMENT=	event-driven I/O for Ruby using the Reactor pattern

DISTNAME=	eventmachine-1.2.0.1
CATEGORIES=	net devel

HOMEPAGE=	http://rubyeventmachine.com/

# ruby or gpl2
PERMIT_PACKAGE_CDROM=	yes

MODULES=	lang/ruby

WANTLIB=	crypto ssl stdc++

CONFIGURE_STYLE=ruby gem ext

MODRUBY_TEST =	rake

TEST_DEPENDS =	${FULLPKGNAME}:${BUILD_PKGPATH}

do-test:
	cd ${WRKSRC} && ${RUBY} -I tests \
		-e 'ARGV.each{|f| require f}' -- ./tests/test_*.rb

.include <bsd.port.mk>
