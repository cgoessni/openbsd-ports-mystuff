# $OpenBSD$

COMMENT =	library and program collection for finite volume simulations

V =			9
EXTRACT_SUFFIX =	.tar.gz
DISTFILES =		version-${V}${EXTRACT_SUFFIX}
DISTNAME =		OpenFOAM-${V}

#GH_ACCOUNT =		OpenFOAM
#GH_PROJECT =		OpenFOAM-${V}

MASTER_SITES =		https://github.com/OpenFOAM/OpenFOAM-${V}/archive/

CATEGORIES =		math

HOMEPAGE =		https://openfoam.org

MAINTAINER =		Clemens Goessnitzer <clemens@goessnitzer.info>

# GPL-2.0
PERMIT_PACKAGE =	Yes

#WANTLIB +=		c execinfo m

RUN_DEPENDS =		shells/bash
LIB_DEPENDS =		math/metis \
			math/scotch \
			devel/openmpi 

USE_GMAKE =		Yes


#CONFIGURE_STYLE =	simple
#CONFIGURE_SCRIPT =	/usr/local/bin/gmake
#CONFIGURE_ARGS +=	config cc=${CC} shared=1 prefix=${LOCALBASE}
#CONFIGURE_ENV +=	LIBVERSION=${LIBmetis_VERSION}

PATCHORIG =		.patch.orig

post-extract:
	#mv ${WRKDIR}/OpenFOAM-${V}-version-${V} ${WRKDIR}/${DISTNAME}
	#find ${WRKSRC} -type f -exec sed -i 's:/bin/bash:/usr/bin/env bash:g' {} +
	mkdir ${WRKSRC}/wmake/rules/openbsd64
	mkdir ${WRKSRC}/wmake/rules/openbsd64Clang

do-build:
	/bin/sh -c ". ${WRKSRC}/etc/bashrc && ${WRKSRC}/Allwmake"

.include <bsd.port.mk>
