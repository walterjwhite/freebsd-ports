# Created by: NAKATA Maho <maho@FreeBSD.org>

PORTNAME=	libEMF
PORTVERSION=	1.0.7
PORTREVISION=	1
CATEGORIES=	graphics
MASTER_SITES=	SF

MAINTAINER=	office@FreeBSD.org
COMMENT=	Enhanced Metafile Library

LICENSE=	LGPL21

BROKEN_riscv64=		fails to build: ../include/libEMF/wine/winnt.h:77:3: Unknown CPU architecture

OPTIONS_DEFINE=	DOCS

USES=		cpe libtool
CPE_VENDOR=	${PORTNAME:tl}_project

GNU_CONFIGURE=	yes

post-install-DOCS-on:
	${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/doc/html/* ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
