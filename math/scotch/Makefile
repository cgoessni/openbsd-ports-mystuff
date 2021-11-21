# $OpenBSD$

COMMENT =		decomposition library for parallel numerical applications

#COMPILER =		ports-gcc

V =			6.1.2
DISTNAME =		scotch-v${V}
PKGNAME =		scotch-${V}

SHARED_LIBS +=		esmumps			0.0
SHARED_LIBS +=		ptscotch		0.0
SHARED_LIBS +=		ptscotcherr		0.0
SHARED_LIBS +=		ptscotcherrexit		0.0
SHARED_LIBS +=		ptscotchparmetis	0.0
SHARED_LIBS +=		scotch			0.0
SHARED_LIBS +=		scotcherr		0.0
SHARED_LIBS +=		scotcherrexit		0.0
SHARED_LIBS +=		scotchmetis		0.0

CATEGORIES =		math

HOMEPAGE =		https://www.labri.fr/perso/pelegrin/scotch/

MAINTAINER =		Clemens Goessnitzer <clemens@goessnitzer.info>

# CeCILL-C V1 (http://www.cecill.info/licences/Licence_CeCILL-C_V1-en.html)
PERMIT_PACKAGE =	Yes

WANTLIB +=		c execinfo m mpi open-pal open-rte pciaccess pthread
WANTLIB +=		util z

MASTER_SITES =		https://gitlab.inria.fr/scotch/scotch/-/archive/v${V}/

WRKSRC =		${WRKDIST}/src

LIB_DEPENDS =		devel/openmpi

USE_GMAKE =		Yes
ALL_TARGET =		scotch ptscotch esmumps

LIBS =
.for lib in ${WANTLIB}
LIBS +=			-l${lib}
.endfor

MAKE_ENV =		prefix="${WRKINST}${PREFIX}" \
			mandir="${WRKINST}${PREFIX}/man" \
			AR="${CC}" \
			ARFLAGS_="-L${LOCALBASE}/lib -L${X11BASE}/lib ${LIBS}" \
			CCS="${CC}" \
			CCD="${CC}" \
			LDFLAGS="-L${LOCALBASE}/lib -L${X11BASE}/lib ${LIBS}" \
			MAKE="${MAKE_PROGRAM}"

post-patch:
	ln -fs Make.inc/Makefile.inc.x86-64_pc_openbsd.shlib \
	    ${WRKSRC}/Makefile.inc

post-build:
.for name in esmumps ptscotch ptscotcherr ptscotcherrexit ptscotchparmetis \
    scotch scotcherr scotcherrexit scotchmetis
	mv ${WRKDIST}/lib/lib${name}.so \
	    ${WRKDIST}/lib/lib${name}.so.${LIB${name}_VERSION}
.endfor

.include <bsd.port.mk>
