PORTNAME=	wireguard-kmod
PORTVERSION=	0.0.20210606
PORTREVISION=	1
CATEGORIES=	net net-vpn
MASTER_SITES=	https://git.zx2c4.com/wireguard-freebsd/snapshot/
DISTNAME=	wireguard-freebsd-${PORTVERSION}

MAINTAINER=	decke@FreeBSD.org
COMMENT=	WireGuard implementation for the FreeBSD kernel

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/../COPYING

USES=		kmod tar:xz uidfix

WRKSRC_SUBDIR=	src

PLIST_FILES=	${KMODDIR}/if_wg.ko

.include <bsd.port.mk>
