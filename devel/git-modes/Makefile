# Created by: KIMURA Yasuhiro <yasu@utahime.org>

PORTNAME=	git-modes
DISTVERSION=	1.4.0
PORTEPOCH=	1
CATEGORIES=	devel elisp
PKGNAMESUFFIX=	${EMACS_PKGNAMESUFFIX}

MAINTAINER=	yasu@FreeBSD.org
COMMENT=	GNU Emacs modes for Git-related files

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/LICENSE

RUN_DEPENDS=	git:devel/git

USES=		emacs gmake
USE_GITHUB=	yes
GH_ACCOUNT=	magit

NO_ARCH=	yes

PLIST_SUB=	ELISPDIR=${_ELISPDIR}
PORTDOCS=	README.md

OPTIONS_DEFINE=	DOCS

_ELISPDIR=	${EMACS_VERSION_SITE_LISPDIR}/${PORTNAME}

do-install:
	@${MKDIR} ${STAGEDIR}${PREFIX}/${_ELISPDIR}
	${INSTALL_DATA} ${WRKSRC}/*.el ${WRKSRC}/*.elc \
		${STAGEDIR}${PREFIX}/${_ELISPDIR}

do-install-DOCS-on:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/README.md ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
