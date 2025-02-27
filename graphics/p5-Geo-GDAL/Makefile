# Created by: Sunpoet Po-Chuan Hsieh <sunpoet@FreeBSD.org>

PORTNAME=	Geo-GDAL
PORTVERSION=	3.3.2
CATEGORIES=	graphics perl5
MASTER_SITES=	https://download.osgeo.org/gdal/${PORTVERSION}/ \
		LOCAL/sunpoet
PKGNAMEPREFIX=	p5-
DISTNAME=	gdal-${PORTVERSION}

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Perl binding for GDAL

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/../../LICENSE.TXT

BUILD_DEPENDS=	p5-Capture-Tiny>=0:devel/p5-Capture-Tiny
LIB_DEPENDS=	libgdal.so:graphics/gdal

USES=		compiler:c++14-lang cpe perl5 tar:xz

USE_CXXSTD=	c++14
WRKSRC_SUBDIR=	swig/perl

CPE_VENDOR=	osgeo
CPE_PRODUCT=	gdal

post-patch:
	@${LN} -s ${LOCALBASE}/bin/gdal-config ${WRKSRC}/../../apps/gdal-config
	@${REINPLACE_CMD} -e 's| INSTALL_BASE=.*||; s| install| pure_install|' ${WRKSRC}/Makefile

# GDALmake.opt is not available until configure phase
post-configure:
	@${SED} -e '/^GDAL_ROOT/d' ${LOCALBASE}/share/gdal/GDALmake.opt > ${WRKSRC}/../../GDALmake.opt

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/${SITE_ARCH_REL}/auto/Geo/GDAL/Const/Const.so ${STAGEDIR}${PREFIX}/${SITE_ARCH_REL}/auto/Geo/*/*.so

.include <bsd.port.mk>
