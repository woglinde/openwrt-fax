#
# Copyright (C) 2006-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libcapi20
PKG_REV:=e23cdd55623a7c4f91a4b01912bb07bd0bf83fdb
PKG_VERSION:=3.25
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://git.misdn.eu/isdn4k-utils
PKG_SOURCE_VERSION:=$(PKG_REV)

PKG_LICENSE:=LGPLv2
PKG_LICENSE_FILES:=COPYING

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/libcapi20/Default
  CATEGORY:=Network
  SECTION:=net
  TITLE:=libcapi
  URL:=https://www.misdn.eu/wiki/Main_Page/
  DEPENDS:=+librt
endef

define Package/libcapi20
$(call Package/libcapi20/Default)
endef

CONFIGURE_PATH:=capi20

MAKE_PATH:=capi20

define Build/InstallDev
        $(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/capi20.h $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/capicmd.h $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/capiutils.h $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/capi_mod.h $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/capi_debug.h $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
                $(PKG_INSTALL_DIR)/usr/lib/libcapi20.{la,a,so*} \
                $(1)/usr/lib/
endef

define Package/libcapi20/install
        $(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
                $(PKG_INSTALL_DIR)/usr/lib/libcapi20.so.* \
                $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libcapi20))

