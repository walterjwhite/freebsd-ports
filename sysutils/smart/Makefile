PORTNAME=	smart
DISTVERSION=	0.3.0
CATEGORIES=	sysutils

MAINTAINER=	jrm@FreeBSD.org
COMMENT=	Output disk SMART values

LICENSE=	ISCL
LICENSE_FILE=	${WRKSRC}/LICENSE

USE_GITHUB=	yes
GH_ACCOUNT=	ctuffli

PLIST_FILES=	sbin/atasmart \
		sbin/nvmesmart \
		sbin/scsismart \
		sbin/smart

post-patch:
	@${REINPLACE_CMD} -e "s|./${PORTNAME}|${PREFIX}/sbin/${PORTNAME}|" \
		${WRKSRC}/[ans]*${PORTNAME}

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/${PORTNAME} ${STAGEDIR}${PREFIX}/sbin
	${INSTALL_SCRIPT} ${WRKSRC}/[ans]*${PORTNAME} ${STAGEDIR}${PREFIX}/sbin

.include <bsd.port.mk>
