# Created by: Igor Vinokurov <igor@zynaps.ru>

PORTNAME=	tac_plus
PORTVERSION=	F4.0.4.28
CATEGORIES=	net security
MASTER_SITES=	ftp://ftp.shrubbery.net/pub/${PORTNAME}/
DISTNAME=	tacacs-${PORTVERSION}

MAINTAINER=	marcus@FreeBSD.org
COMMENT=	Cisco remote authentication/authorization/accounting server

GNU_CONFIGURE=	yes
USES=		bison cpe perl5 libtool
USE_PERL5=	build
USE_RC_SUBR=	tac_plus
USE_LDCONFIG=	yes
CONFIGURE_ARGS=	--with-groupid=$$(/usr/bin/id -g tacacs 2>/dev/null || echo '559') \
		--with-userid=$$(/usr/bin/id -u tacacs 2>/dev/null || echo '559')

CPE_VENDOR=	cisco

USERS=		tacacs
GROUPS=		tacacs

CONFLICTS=	ru-tac+ia-[0-9]* tac_plus-libradius-[0-9]*
MAKE_JOBS_UNSAFE=	yes

OPTIONS_DEFINE=	DOCS

# check expiration dates against 'expire' field of master.passwd file
.if defined(TAC_EXPIRE_MASTER_PASSWD)
EXTRA_PATCHES+=	${PATCHDIR}/extra-patch-bb
.endif

.if exists(/usr/include/skey.h) && !defined(WITHOUT_SKEY)
CONFIGURE_ARGS+=	--with-skey
.else
CONFIGURE_ARGS+=	--without-skey
.endif

.if exists(/usr/include/opie.h) && !defined(WITHOUT_OPIE)
CPPFLAGS+=	-DOPIE
LIBS+=		-lopie -lmd
.endif

post-patch:
	@${REINPLACE_CMD} -e 's|skey_get_algorithm|skeychallenge|g' \
		${WRKSRC}/configure

post-install:
	${INSTALL_DATA} ${FILESDIR}/tac_plus.conf.example ${STAGEDIR}${PREFIX}/etc
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/doc/tac_plus
	${INSTALL_DATA} ${WRKSRC}/users_guide ${STAGEDIR}${PREFIX}/share/doc/tac_plus
	${INSTALL_SCRIPT} ${WRKSRC}/tac_convert ${STAGEDIR}${PREFIX}/share/doc/tac_plus

.include <bsd.port.mk>
