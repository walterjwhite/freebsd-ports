PORTNAME=	openvdb
DISTVERSIONPREFIX=	v
DISTVERSION=	8.1.0
PORTREVISION=	6
CATEGORIES=	misc

PATCH_SITES=	https://github.com/${GH_ACCOUNT}/${PORTNAME}/commit/
PATCHFILES=	e620aa6a472e7e5bebaf2103ed2b4d6442438341.patch:-p1 # backport of change TBB -> OneTBB

MAINTAINER=	yuri@FreeBSD.org
COMMENT=	Tools for storage and manipulation of sparse volumetric data

LICENSE=	MPL20
LICENSE_FILE=	${WRKSRC}/LICENSE

LIB_DEPENDS=	libblosc.so:archivers/c-blosc \
		libboost_system.so:devel/boost-libs \
		libImath.so:math/Imath \
		libtbb.so:devel/onetbb
TEST_DEPENDS=	googletest>0:devel/googletest

USES=		cmake:testing compiler:c++11-lang localbase:ldflags pkgconfig
USE_LDCONFIG=	yes

USE_GITHUB=	yes
GH_ACCOUNT=	AcademySoftwareFoundation

CMAKE_ARGS=		-DCONCURRENT_MALLOC="Tbbmalloc" -DTbb_INCLUDE_DIR=${LOCALBASE}/include
CMAKE_OFF=		OPENVDB_CORE_STATIC
CMAKE_TESTING_ON=	OPENVDB_BUILD_UNITTESTS # one test fails: https://github.com/AcademySoftwareFoundation/openvdb/issues/1103

OPTIONS_DEFINE=		PYTHON TOOLS #DOCS # TOOLS and PYTHON should be made into subpackages
OPTIONS_DEFAULT=	PYTHON TOOLS
OPTIONS_SUB=		yes

PYTHON_USES=		python
PYTHON_CMAKE_BOOL=	OPENVDB_BUILD_PYTHON_MODULE
PYTHON_CMAKE_ON=	-DFREEBSD_PYTHON_VER:STRING=${PYTHON_VER} -DUSE_NUMPY:BOOL=ON
PYTHON_LIB_DEPENDS=	${PY_BOOST}
PYTHON_BUILD_DEPENDS=	${PYNUMPY}
PYTHON_RUN_DEPENDS=	${PYNUMPY}

TOOLS_DESC=		Build CLI tools
TOOLS_CMAKE_BOOL=	OPENVDB_BUILD_BINARIES OPENVDB_BUILD_VDB_LOD \
			OPENVDB_BUILD_VDB_RENDER OPENVDB_BUILD_VDB_VIEW
TOOLS_LIB_DEPENDS=	libglfw.so:graphics/glfw \
			libOpenEXR.so:graphics/openexr
TOOLS_USES=		gl xorg
TOOLS_USE=		GL=gl,glu XORG=ice,sm,x11,xcursor,xext,xi,xinerama,xrandr,xxf86vm

post-patch: # extra fix for OneTBB
	@cd ${WRKSRC}/openvdb/openvdb && \
		${MKDIR} thread && \
		${MV} util/Threading.h thread/

# DOCS is broken: https://github.com/AcademySoftwareFoundation/openvdb/issues/899
#DOCS_CMAKE_BOOL=	OPENVDB_BUILD_DOCS
#DOCS_BUILD_DEPENDS=	doxygen:devel/doxygen

#PORTDOCS=	*

.include <bsd.port.mk>
