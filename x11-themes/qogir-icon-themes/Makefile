# Created by: Alexander Vereeken <Alexander88207@protonmail.com>

PORTNAME=	qogir-icon-themes
DISTVERSION=	2021-07-14
CATEGORIES=	x11-themes

MAINTAINER=	Alexander88207@protonmail.com
COMMENT=	Flat colorful design icon theme for linux desktops

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/COPYING

BUILD_DEPENDS=	bash>0:shells/bash \
		gsed:textproc/gsed

USES=		shebangfix
SHEBANG_FILES=	install.sh

USE_GITHUB=	yes
GH_ACCOUNT=	vinceliuice
GH_PROJECT=	Qogir-icon-theme
NO_ARCH=	yes
NO_BUILD=	yes
BINARY_ALIAS=	gtk-update-icon-cache=${TRUE}

do-install:
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/icons
	${SETENV} PATH="${PATH}" ${WRKSRC}/install.sh -d ${STAGEDIR}${PREFIX}/share/icons

.include <bsd.port.mk>
