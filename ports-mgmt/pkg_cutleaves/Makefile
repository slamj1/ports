# Created by: Stefan Walter <sw@gegenunendlich.de>
# $FreeBSD$

PORTNAME=	pkg_cutleaves
PORTVERSION=	20090810
CATEGORIES=	ports-mgmt
MASTER_SITES=	# none
DISTFILES=	# none

MAINTAINER=	bofh@FreeBSD.org
COMMENT=	Interactive script for deinstalling 'leaf' packages

EXPLICIT_SAFESTACK=		yes

LICENSE=	BSD2CLAUSE

NO_BUILD=	yes
USES=		perl5 shebangfix
SHEBANG_FILES=	pkg_cutleaves
NO_WRKSUBDIR=	yes

PLIST_FILES=	sbin/pkg_cutleaves man/man1/pkg_cutleaves.1.gz

do-extract:
	${MKDIR} ${WRKSRC}
	${CP} ${FILESDIR}/pkg_cutleaves ${FILESDIR}/pkg_cutleaves.1 ${WRKSRC}

post-patch:
	@${REINPLACE_CMD} -e \
	  's,/usr/local/etc/pkg_leaves.exclude,${PREFIX}/etc/pkg_leaves.exclude,' \
	  ${WRKSRC}/pkg_cutleaves.1
	@${REINPLACE_CMD} \
	  -e 's,/usr/local/etc/pkg_leaves.exclude,${PREFIX}/etc/pkg_leaves.exclude,' \
	  -e 's,/usr/local/sbin/pkg delete -y,${PKG_DELETE},' \
	  -e 's,/usr/local/sbin/pkg query,${PKG_QUERY},' \
	  ${WRKSRC}/pkg_cutleaves

do-install:
	${INSTALL_SCRIPT} ${WRKSRC}/pkg_cutleaves ${STAGEDIR}${PREFIX}/sbin/pkg_cutleaves
	${INSTALL_MAN} ${WRKSRC}/pkg_cutleaves.1 ${STAGEDIR}${MAN1PREFIX}/man/man1

.include <bsd.port.mk>
