#
# Copyright (C) 2006-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=misdn-user
PKG_REV:=df131f57d4d5f75081b3bae75268d69ea21491eb
PKG_VERSION:=2.0.17
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://git.misdn.eu/mISDNuser.git
PKG_SOURCE_VERSION:=$(PKG_REV)

#PKG_LICENSE:=LGPLv2
#PKG_LICENSE_FILES:=COPYING

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

CONFIGURE_ARGS += \
	--disable-example \
	--disable-gui \
	--disable-memleak_debug \
	--enable-capi \
	--enable-softdsp \
        --with-AF_ISDN=34

define Package/misdn-user/Default
  CATEGORY:=Network
  SECTION:=net
  TITLE:=utils for misdn and libcapi
  URL:=https://www.misdn.eu/wiki/Main_Page/
endef

define Package/misdn-user
$(call Package/misdn-user/Default)
  DEPENDS:=+libspandsp +libcapi20
endef

define Package/misdn-user/InstallDev
        $(INSTALL_DIR) $(1)/usr/include
endef

define Package/misdn-user/install
        $(INSTALL_DIR) $(1)/usr/lib
endef

$(eval $(call BuildPackage,misdn-user))

