# Created by: Andrew Pantyukhin <infofarmer@FreeBSD.org>

PORTNAME=	aria2
PORTVERSION=	1.36.0
CATEGORIES=	www
MASTER_SITES=	https://github.com/aria2/aria2/releases/download/release-${PORTVERSION}/ \
		LOCAL/sunpoet

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Yet another download tool

LICENSE=	GPLv2
LICENSE_FILE=	${WRKSRC}/COPYING

USES=		compiler:c++11-lib cpe libtool pathfix pkgconfig ssl tar:xz

CONFIGURE_ARGS=	--disable-epoll \
		--enable-bittorrent --enable-libaria2 --enable-metalink --enable-shared --enable-ssl --enable-threads=posix --enable-websocket \
		--with-disk-cache=${ARIA2_DISK_CACHE} \
		--with-libz --with-openssl \
		--without-appletls --without-gnutls --without-libgcrypt --without-libgmp --without-libnettle
CONFIGURE_ENV=	OPENSSL_CFLAGS=-I${OPENSSLINC} \
		OPENSSL_LIBS="-L${OPENSSLLIB} -lcrypto -lssl" \
		ac_cv_path_RST2HTML=no
GNU_CONFIGURE=	yes
INSTALL_TARGET=	install-strip
USE_CXXSTD=	c++11
USE_LDCONFIG=	yes
USE_RC_SUBR=	aria2

PORTDOCS=	*

ARIA2_DISK_CACHE?=	16M

CPE_VENDOR=	aria2_project

OPTIONS_DEFINE=	CA_BUNDLE CARES DOCS LIBUV NLS SQLITE SSH2 STATIC
OPTIONS_SINGLE=	XML
OPTIONS_SINGLE_XML=	EXPAT LIBXML2
OPTIONS_DEFAULT=CA_BUNDLE LIBXML2 SQLITE STATIC
OPTIONS_SUB=	yes
CA_BUNDLE_DESC=	Use CA bundle from Mozilla Project
LIBUV_DESC=	Event polling via libuv
SSH2_DESC=	SSH2 protocol support

CA_BUNDLE_CONFIGURE_OFF=--without-ca-bundle
CA_BUNDLE_CONFIGURE_ON=	--with-ca-bundle=${LOCALBASE}/share/certs/ca-root-nss.crt
CA_BUNDLE_RUN_DEPENDS=	${LOCALBASE}/share/certs/ca-root-nss.crt:security/ca_root_nss
CARES_CONFIGURE_WITH=	libcares
CARES_LIB_DEPENDS=	libcares.so:dns/c-ares
EXPAT_CONFIGURE_WITH=	libexpat
EXPAT_LIB_DEPENDS=	libexpat.so:devel/expat2
LIBUV_CONFIGURE_WITH=	libuv
LIBUV_LIB_DEPENDS=	libuv.so:devel/libuv
LIBXML2_CONFIGURE_WITH=	libxml2
LIBXML2_USE=		GNOME=libxml2
LIBXML2_USES=		gnome
NLS_CONFIGURE_OFF=	--disable-nls --without-libintl-prefix
NLS_CONFIGURE_ON=	--with-libintl-prefix=${LOCALBASE}
NLS_LDFLAGS=		-lintl
NLS_USES=		gettext localbase
SQLITE_CONFIGURE_WITH=	sqlite3
SQLITE_USES=		sqlite
SSH2_CONFIGURE_WITH=	libssh2
SSH2_LIB_DEPENDS=	libssh2.so:security/libssh2
STATIC_CONFIGURE_ENABLE=static

post-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/bash_completion.d/
	${INSTALL_DATA} ${WRKSRC}/doc/bash_completion/aria2c ${STAGEDIR}${PREFIX}/etc/bash_completion.d/

.include <bsd.port.mk>
