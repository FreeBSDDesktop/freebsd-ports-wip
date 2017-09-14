# Created by: Dmitry Marakasov <amdmi3@FreeBSD.org>
# $FreeBSD$

PORTNAME=	notion
PORTVERSION=	g20170912
CATEGORIES=	x11-wm

MAINTAINER=	jmd@FreeBSD.org
COMMENT=	Tiling tabbed window manager

LICENSE=	LGPL21
LICENSE_FILE=	${WRKSRC}/LICENSE

USE_GITHUB=	yes
GH_ACCOUNT=	raboof
GH_TAGNAME=	e0ab8a2

USE_XORG=	ice sm x11 xext xft
USES=		gettext gmake lua pkgconfig
MAKE_ENV=	LUA_VERSION=${LUA_VER}

PORTDOCS=	*

OPTIONS_DEFINE=	XINERAMA XRANDR DOCS
OPTIONS_DEFAULT=XINERAMA XRANDR
OPTIONS_SUB=	yes

XINERAMA_DESC=	Xinerama module support
XINERAMA_USE=	XORG=xinerama
XRANDR_DESC=	Xrandr module support
XRANDR_USE=	XORG=xrandr

post-patch-DOCS-off:
	@${REINPLACE_CMD} -e '/^_install:/,/^$$/ d' ${WRKSRC}/Makefile

post-patch-XINARAMA-off:
	@${REINPLACE_CMD} -e 's|mod_xinerama||' ${WRKSRC}/modulelist.mk

post-patch-XRANDR-off:
	@${REINPLACE_CMD} -e 's|mod_xrandr||' ${WRKSRC}/modulelist.mk

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/notion \
		${STAGEDIR}${PREFIX}/lib/notion/bin/* \
		${STAGEDIR}${PREFIX}/lib/notion/mod/*.so

.include <bsd.port.mk>
