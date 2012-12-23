#
# Copyright (C) 2006-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=capiinfo
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

define Package/capiinfo/Default
  CATEGORY:=Network
  SECTION:=net
  TITLE:=capiinfo
  URL:=https://www.misdn.eu/wiki/Main_Page/
  DEPENDS:=+libcapi20
endef

define Package/capiinfo
$(call Package/capiinfo/Default)
endef

CONFIGURE_PATH:=capiinfo

MAKE_PATH:=capiinfo

define Package/capiinfo/install
        $(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/capiinfo $(1)/usr/bin/
endef

$(eval $(call BuildPackage,capiinfo))

