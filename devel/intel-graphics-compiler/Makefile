PORTNAME=	intel-graphics-compiler
DISTVERSIONPREFIX=	igc-
DISTVERSION=	1.0.8744
CATEGORIES=	devel
PKGNAMESUFFIX=	-${FLAVOR}

MAINTAINER=	jbeich@FreeBSD.org
COMMENT=	Intel Graphics Compiler for OpenCL

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE.md

ONLY_FOR_ARCHS=	amd64 i386
ONLY_FOR_ARCHS_REASON=	only Intel GPUs on x86 are supported

BUILD_DEPENDS=	vc-intrinsics-${FLAVOR}>=s20210730:devel/vc-intrinsics@${FLAVOR}
LIB_DEPENDS=	libopencl-clang.so.${FLAVOR:S/llvm//}:devel/opencl-clang@${FLAVOR}

FLAVORS=	${12 11:L:S/^/llvm/}

CONFLICTS_INSTALL=	${PORTNAME}-*

USES=		bison cmake compiler:c++17-lang python:build
USE_GITHUB=	yes
USE_LDCONFIG=	yes
GH_ACCOUNT=	intel
CMAKE_OFF=	INSTALL_SPIRVDLL
CMAKE_ARGS=	-DCMAKE_PREFIX_PATH:PATH="${LOCALBASE}/${FLAVOR}" \
		-DIGC_OPTION__LLVM_PREFERRED_VERSION:STRING="${FLAVOR:S/llvm//}"
CFLAGS+=	-Wno-macro-redefined # __fastcall
PLIST_SUB=	ARCH_SUFX=${ARCH:S/i386/32/:S/amd//:S/x86_//}

post-patch:
# lang/python* don't install unsuffixed symlinks
	@${REINPLACE_CMD} -i .python \
		-e '/EXECUTABLE/s/"python"/"${PYTHON_CMD:T}"/' \
		-e '/IGC_PYTHON/s/"python"/"${PYTHON_CMD:T}"/' \
		${WRKSRC}/IGC/CMakeLists.txt \
		${WRKSRC}/IGC/BiFModule/linux/CMakeLists.txt
# No need to abort on every benign warning enabled by default
# Disable debug symbols unless WITH_DEBUG passed via CXXFLAGS
	@${REINPLACE_CMD} -e 's/"-Werror"//; /-Werror/d' \
		-e 's/"-g"//' \
		${WRKSRC}/IGC/CMakeLists.txt

.include <bsd.port.mk>
