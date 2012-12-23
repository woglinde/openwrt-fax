#
# Copyright (C) 2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=cppcms
PKG_VERSION:=1.0.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@SF/cppcms
PKG_MD5SUM:=29602aad2d18d869f1d75360b14411b4

CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/cppcms/Default
  TITLE:=cppcms is a c++ framework for http applications
  URL:=http://cppcms.com
endef

define Package/cppcms/Default/description
  cppcms is web application server written
  in c++. It as a small footprint in size
  and works stanalone no extra webserver is needed.
endef

define Package/cppcms
  $(call Package/cppcms/Default)
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Web Servers/Proxies
  DEPENDS:=+libpcre +libpthread
endef

CMAKE_OPTIONS += \
		-DDISABLE_ICU_LOCALE=true \
		-DDISABLE_ICONV=true \
		-DDISABLE_POSIX_LOCALE=true

define Package/cppcms/description
  $(call Package/cppcms/Default/description)
endef

define Build/InstallDev
        $(INSTALL_DIR) $(1)/usr/include/booster
        $(INSTALL_DIR) $(1)/usr/include/cppcms
        $(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/include/booster/* $(1)/usr/include/booster/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/include/cppcms/*.h $(1)/usr/include/cppcms/

        $(INSTALL_DIR) $(1)/usr/lib
        $(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/libbooster.{a,so*} $(1)/usr/lib/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/libcppcms.{a,so*} $(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/bin/cppcms_tmpl_cc $(1)/usr/bin/
endef

define Package/cppcms/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/libbooster.{a,so*} $(1)/usr/lib/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/libcppcms.{a,so*} $(1)/usr/lib/
endef

$(eval $(call BuildPackage,cppcms))
