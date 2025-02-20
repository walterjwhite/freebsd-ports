PORTNAME=	pkg
DISTVERSION=	1.17.99.7
_PKG_VERSION=	${DISTVERSION}
CATEGORIES=	ports-mgmt
PKGNAMESUFFIX=	-devel

MAINTAINER=	pkg@FreeBSD.org
COMMENT=	Package manager

LICENSE=	BSD2CLAUSE

USE_GITHUB=	yes
GH_ACCOUNT=	freebsd
GH_TAGNAME=	fd770b1e

CFLAGS+=	-O0 -g -Wno-error
USE_LDCONFIG=	${PREFIX}/lib/compat/pkg
HAS_CONFIGURE=	yes
PORTDOCS=	NEWS
PORTSCOUT=	ignore:1
CONFIGURE_ARGS=	--mandir=${PREFIX}/man --prefix="${PREFIX}"
CONFIGURE_ENV=	CC_FOR_BUILD="${CC}"

# Use a submake as 'deinstall install' needs to reevaluate PKG_REGISTER
# so that pkg-static is used from the wrkdir
USE_SUBMAKE=	yes

OPTIONS_DEFINE=	DOCS SAN
SAN_DESC=	Enable sanitizers (ASAN and UBSAN)

.if !exists(/usr/include/jail.h)
EXTRA_PATCHES=	${FILESDIR}/extra-patch-docs_pkg.8
.endif

.include <bsd.port.pre.mk>

.if ${PORT_OPTIONS:MSAN}
CONFIGURE_ARGS+=	--with-asan --with-ubsan
.endif

# TODO: activate in april 2021
#.if ${OPSYS} == FreeBSD && ${OSVERSION} > 1400000
#CONFIGURE_ARGS+=	--default-format=tzst
#.endif

.if !exists(/usr/libdata/pkgconfig/liblzma.pc)
LIBLZMA_LIBS=	-llzma
.else
LIBLZMA_PC!=	${EGREP} ^Libs /usr/libdata/pkgconfig/liblzma.pc
LIBLZMA_LIBS=	${LIBLZMA_PC:M-l*}
.endif

.if defined(WITH_PKG)
.if ${WITH_PKG} != devel
.	if !defined(PACKAGE_BUILDING)
IGNORE=	WITH_PKG is not defined to 'devel', this version is the devel one
.	endif
.else
PKGNAMESUFFIX=
#define PKG_DEPENDS to nothing to avoid infinite loop looking for pkg :)
PKG_DEPENDS=
.endif
.endif

.undef INSTALLS_DEPENDS
.if !exists(${LOCALBASE}/sbin/pkg) && !defined(CROSS_TOOLCHAIN)
PKG_BIN=	${WRKSRC}/src/pkg-static
.endif

post-patch:
	${REINPLACE_CMD} -e "s|-llzma|${LIBLZMA_LIBS}|g" ${WRKSRC}/auto.def \
		${WRKSRC}/src/Makefile.autosetup ${WRKSRC}/tests/Makefile.autosetup

.if ${PORT_OPTIONS:MSAN}
post-build:
	@(cd ${WRKSRC}/src && \
		${LN} -fs pkg pkg-static)
.endif

post-install:
	@${MKDIR} ${STAGEDIR}${PREFIX}/lib/compat/pkg
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/NEWS ${STAGEDIR}${DOCSDIR}/NEWS
.if ${PORT_OPTIONS:MSAN}
	@${CP} ${STAGEDIR}${PREFIX}/sbin/pkg ${STAGEDIR}${PREFIX}/sbin/pkg-static
.endif

.include <bsd.port.post.mk>
