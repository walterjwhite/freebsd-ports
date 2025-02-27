# Created by: Po-Chuan Hsieh <sunpoet@FreeBSD.org>

PORTNAME=	pyspnego
PORTVERSION=	0.3.0
CATEGORIES=	security python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Windows Negotiate Authentication Client and Server

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}cryptography>=0:security/py-cryptography@${PY_FLAVOR}

USES=		python:3.6+
USE_PYTHON=	autoplist concurrent distutils

NO_ARCH=	yes

OPTIONS_DEFINE=	KERBEROS YAML
KERBEROS_DESC=	Kerberos authentication support
YAML_DESC=	YAML output support

KERBEROS_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}gssapi>=1.5.0:security/py-gssapi@${PY_FLAVOR} \
			${PYTHON_PKGNAMEPREFIX}krb5>=0:security/py-krb5@${PY_FLAVOR}
YAML_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}ruamel.yaml>=0:devel/py-ruamel.yaml@${PY_FLAVOR}

.include <bsd.port.pre.mk>

.if ${PYTHON_REL} < 30700
RUN_DEPENDS+=	${PYTHON_PKGNAMEPREFIX}dataclasses>=0:devel/py-dataclasses@${PY_FLAVOR}
.endif

.include <bsd.port.post.mk>
