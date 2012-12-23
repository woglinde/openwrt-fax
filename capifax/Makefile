#
# Copyright (C) 2006-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=capifax
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

define Package/capifax/Default
  CATEGORY:=Network
  SECTION:=net
  TITLE:=libcapi
  URL:=https://www.misdn.eu/wiki/Main_Page/
  DEPENDS:=+libcapi20
endef

define Package/capifax
$(call Package/capifax/Default)
endef

CONFIGURE_PATH:=capifax

MAKE_PATH:=capifax

define Package/capifax/install
        $(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/capifax $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/sbin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/capifaxrcvd $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,capifax))

