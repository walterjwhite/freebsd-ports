# Created by: Sevan Janiyan <venture37@geeklan.co.uk>

PORTNAME=	chillispot
PORTVERSION=	1.0
PORTREVISION=	12
CATEGORIES=	net-mgmt
MASTER_SITES=	http://www.chillispot.info/download/ \
		http://www.geeklan.co.uk/files/ \
		http://www.venture37.com/files/

MAINTAINER=	venture37@geeklan.co.uk
COMMENT=	Wireless LAN Access Point Controller

CONFLICTS=	coovachilli-[0-9]*

USES=		compiler:nestedfct shebangfix
SHEBANG_FILES=	doc/hotspotlogin.cgi
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=-sysconfdir=${PREFIX}/etc
USE_RC_SUBR=	chillispot
SUB_FILES=	pkg-message installguide.txt

OPTIONS_DEFINE=		APACHE RADIUS
OPTIONS_SINGLE=		RADIUS
OPTIONS_SINGLE_RADIUS=	FREERADIUS OPENRADIUS

FREERADIUS_DESC=depend on FreeRADIUS
OPENRADIUS_DESC=depend on OpenRADIUS

APACHE_USE=	apache_run=22+
FREERADIUS_RUN_DEPENDS=	radiusd:net/freeradius
OPENRADIUS_RUN_DEPENDS=	radiusd:net/openradius

.include <bsd.port.pre.mk>

.if ${CHOSEN_COMPILER_TYPE} == gcc && ${COMPILER_VERSION} <= 42
CFLAGS+=	-fnested-functions
.endif

post-install:
	${MKDIR} ${STAGEDIR}${DATADIR}
	${INSTALL_DATA} ${WRKSRC}/doc/chilli.conf ${STAGEDIR}${DATADIR}/chilli.conf.sample
	${INSTALL_DATA} ${WRKSRC}/doc/dictionary.chillispot ${STAGEDIR}${DATADIR}
	${INSTALL_DATA} ${WRKSRC}/doc/freeradius.users ${STAGEDIR}${DATADIR}
	${INSTALL_DATA} ${WRKSRC}/doc/hotspotlogin.cgi ${STAGEDIR}${DATADIR}
	${INSTALL_DATA} ${WRKDIR}/installguide.txt ${STAGEDIR}${DATADIR}
	${INSTALL_DATA} ${FILESDIR}/pf.conf.sample ${STAGEDIR}${DATADIR}
	${INSTALL_DATA} ${FILESDIR}/ipfw-config.sample ${STAGEDIR}${DATADIR}

.include <bsd.port.post.mk>
