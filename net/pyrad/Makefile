# Created by: Blaz Zupan <blaz@si.FreeBSD.org>

PORTNAME=	pyrad
PORTVERSION=	2.0
PORTREVISION=	1
CATEGORIES=	net python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	steve@energistic.com
COMMENT=	Python implementation of RADIUS client

USES=		cpe python:3.6+
USE_PYTHON=	distutils autoplist

CPE_VENDOR=	pyrad_project

PORTEXAMPLES=	*

OPTIONS_DEFINE=	EXAMPLES

.include <bsd.port.options.mk>

post-patch:
	@${REINPLACE_CMD} -e 's|zip_safe=True|zip_safe=False|' \
		${WRKSRC}/setup.py

.if ${PORT_OPTIONS:MEXAMPLES}
post-install:
	@${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
	(cd ${WRKSRC}/example && ${COPYTREE_SHARE} . ${STAGEDIR}${EXAMPLESDIR})
.endif

.include <bsd.port.mk>
