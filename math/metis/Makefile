# $OpenBSD$

COMMENT =	serial graph partitioning and fill-reducing matrix ordering

DISTNAME =	metis-5.1.0

SHARED_LIBS +=	metis	0.0	# 5.1.0

CATEGORIES =	math

HOMEPAGE =	http://glaros.dtc.umn.edu/gkhome/metis/metis/overview

MAINTAINER =	Clemens Goessnitzer <clemens@goessnitzer.info>

# Apache-2.0
PERMIT_PACKAGE = Yes

WANTLIB +=	c execinfo m

MASTER_SITES =	http://glaros.dtc.umn.edu/gkhome/fetch/sw/metis/

MODULES =	devel/cmake

CONFIGURE_ARGS +=	-DGKLIB_PATH=${WRKSRC}/GKlib \
			-DSHARED=1

NO_TEST =	Yes

.include <bsd.port.mk>
