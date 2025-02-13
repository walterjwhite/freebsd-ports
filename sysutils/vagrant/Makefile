# Created by: Joseph Benden <joe@thrallingpenguin.com>

PORTNAME=	vagrant
PORTVERSION=	2.2.14
DISTVERSIONPREFIX=	v
PORTREVISION=	5
CATEGORIES=	sysutils rubygems devel

MAINTAINER=	joe@thrallingpenguin.com
COMMENT=	Vagrant Virtual Machine Manager

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	rubygem-builder>=2.1.2:devel/rubygem-builder \
		rubygem-bundler>=1.12.5:sysutils/rubygem-bundler \
		rubygem-main>=1.0:devel/rubygem-main
RUN_DEPENDS=	rubygem-bcrypt_pbkdf10>=1.0.0<1.1:security/rubygem-bcrypt_pbkdf10 \
		rubygem-bundler>=1.12.5:sysutils/rubygem-bundler \
		rubygem-childprocess40>=4.0.0<4.1.0:devel/rubygem-childprocess40 \
		rubygem-ed25519>=1.2.4<1.3:security/rubygem-ed25519 \
		rubygem-erubis>=2.7.0<2.8:www/rubygem-erubis \
		rubygem-excon>=0.73<1.0:devel/rubygem-excon \
		rubygem-hashicorp-checkpoint>=0.1.5<0.2:www/rubygem-hashicorp-checkpoint \
		rubygem-i18n>=1.8,2<2,2:devel/rubygem-i18n \
		rubygem-listen>=3.1.5:devel/rubygem-listen \
		rubygem-log4r>=1.1.9<1.1.11:sysutils/rubygem-log4r \
		rubygem-net-scp1>=1.2.0<1.3:security/rubygem-net-scp1 \
		rubygem-net-sftp2>=2.1<3:security/rubygem-net-sftp2 \
		rubygem-net-ssh>=5.2.0:security/rubygem-net-ssh \
		rubygem-rb-kqueue>=0.2.0<0.3:devel/rubygem-rb-kqueue \
		rubygem-rest-client>=1.6.0<3.0:www/rubygem-rest-client \
		rubygem-rubyzip>=2.2<3:archivers/rubygem-rubyzip \
		rubygem-vagrant_cloud>=3.0.2<3.1:sysutils/rubygem-vagrant_cloud \
		rubygem-wdm>=0.1.0<0.2:devel/rubygem-wdm \
		rubygem-winrm>=2.3.4<3:sysutils/rubygem-winrm \
		rubygem-winrm-elevated>=1.2.1<2:sysutils/rubygem-winrm-elevated \
		rubygem-winrm-fs>=1.3.4<2:sysutils/rubygem-winrm-fs \
		rubygem-ruby_dep>=0:devel/rubygem-ruby_dep \
		ca_root_nss>=0:security/ca_root_nss \
		curl:ftp/curl

USE_GITHUB=	yes
GH_ACCOUNT=	hashicorp

USES=		cpe shebangfix
CPE_VENDOR=	hashicorp
SHEBANG_FILES=	plugins/hosts/darwin/scripts/install_virtualbox.sh \
		scripts/sign.sh \
		scripts/website_push_www.sh
USE_RUBY=	yes
GEMFILES=	vagrant-${PORTVERSION}.gem
RUBYGEMBIN=	gem${RUBY_SUFFIX}
PLIST_SUB+=	GEMS_DIR="lib/ruby/gems/${RUBY_VER}/" \
		GEM_BASE_DIR="lib/ruby/gems/${RUBY_VER}/gems" \
		DOC_DIR="lib/ruby/gems/${RUBY_VER}/doc" \
		PORTVERSION="${PORTVERSION}"
NO_ARCH=	yes

RUBYGEM_ARGS=	-l --no-document --no-update-sources \
		--install-dir ${STAGEDIR}${PREFIX}/lib/ruby/gems/${RUBY_VER} \
		--ignore-dependencies --bindir=${STAGEDIR}${PREFIX}/bin
GEM_ENV+=	RB_USER_INSTALL=yes

OPTIONS_DEFINE=		BASH ZSH
OPTIONS_DEFAULT=	BASH ZSH

BASH_PLIST_FILES=	share/bash-completion/completions/vagrant
ZSH_PLIST_FILES=	share/share/zsh/site-functions/_vagrant

post-patch:
	@${REINPLACE_CMD} -e 's|@PREFIX@|${PREFIX}|g' ${WRKSRC}/bin/vagrant

do-build:
	(cd ${WRKSRC}; (${ECHO_CMD} -e "install:\n\techo\n") > Makefile)
	(cd ${WRKSRC}; ${SETENV} VAGRANT_INSTALLER_ENV=yes \
		${GEM_ENV} ${RUBYGEMBIN} build vagrant.gemspec)
	(cd ${WRKSRC}; ${SETENV} VAGRANT_INSTALLER_ENV=yes \
		${GEM_ENV} ${RUBYGEMBIN} install ${RUBYGEM_ARGS} \
		${GEMFILES} -- ${CONFIGURE_ARGS})
	${RMDIR} ${STAGEDIR}${PREFIX}/lib/ruby/gems/${RUBY_VER}/build_info
	${MKDIR} ${STAGEDIR}${DATADIR}/embedded/rgloader
	${INSTALL_SCRIPT} ${FILESDIR}/loader.rb \
		${STAGEDIR}${DATADIR}/embedded/rgloader/loader.rb

post-install:
	${RMDIR} ${STAGEDIR}${PREFIX}/lib/ruby/gems/${RUBY_VER}/doc
	${RM} ${STAGEDIR}${PREFIX}/lib/ruby/gems/${RUBY_VER}/gems/${PORTNAME}-${PORTVERSION}/.runner.sh

post-install-BASH-on:
	${MKDIR} ${STAGEDIR}${PREFIX}/share/bash-completion/completions
	${RLN} ${STAGEDIR}${PREFIX}/lib/ruby/gems/${RUBY_VER}/gems/${PORTNAME}-${PORTVERSION}/contrib/bash/completion.sh ${STAGEDIR}${PREFIX}/share/bash-completion/completions/vagrant

post-install-ZSH-on:
	${MKDIR} ${STAGEDIR}${PREFIX}/share/share/zsh/site-functions
	${RLN} ${STAGEDIR}${PREFIX}/lib/ruby/gems/${RUBY_VER}/gems/${PORTNAME}-${PORTVERSION}/contrib/zsh/_vagrant ${STAGEDIR}${PREFIX}/share/share/zsh/site-functions

.include <bsd.port.mk>
