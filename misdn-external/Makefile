#
# Copyright (C) 2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=misdn-external
PKG_REV:=c7bbed79825ff9e5298e34e2b2b6c971e9865934
PKG_VERSION:=3.3
PKG_RELEASE:=1
PKG_FIXUP:=autoreconf

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://git.misdn.eu/mISDN.git
PKG_SOURCE_VERSION:=$(PKG_REV)

PKG_BUILD_PARALLEL:=1
PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

MISDN_FILES:= \
	$(PKG_BUILD_DIR)/standalone/drivers/isdn/mISDN/mISDN_dsp_oslec.ko \
	$(PKG_BUILD_DIR)/standalone/drivers/isdn/mISDN/mISDN_dsp.ko \
	$(PKG_BUILD_DIR)/standalone/drivers/isdn/mISDN/octvqe/octvqe.ko \
	$(PKG_BUILD_DIR)/standalone/drivers/isdn/mISDN/mISDN_dsp_mec2.ko \
	$(PKG_BUILD_DIR)/standalone/drivers/isdn/mISDN/mISDN_dsp_mg2ec.ko \
	$(PKG_BUILD_DIR)/standalone/drivers/isdn/mISDN/mISDN_core.ko \
	$(PKG_BUILD_DIR)/standalone/drivers/isdn/mISDN/mISDN_dsp_kb1ec.ko \
	$(PKG_BUILD_DIR)/standalone/drivers/isdn/mISDN/mISDN_dsp_octwareec.ko \
	$(PKG_BUILD_DIR)/standalone/drivers/isdn/mISDN/l1oip.ko \
	$(PKG_BUILD_DIR)/standalone/drivers/isdn/hardware/mISDN/hfcsusb.ko

define KernelPackage/misdn-external
  SUBMENU:=Network Support
  TITLE:=out of tree misdn modules
  URL:=https://www.misdn.eu/wiki/Main_Page/
  FILES:=$(MISDN_FILES)
endef

include $(INCLUDE_DIR)/kernel-defaults.mk

define KernelPackage/misdn-external/description
  Out of tree misdn kernel modules
endef

define Build/Configure
	$(call Build/Configure/Default,--with-kerneldir=$(LINUX_DIR))
	( cd $(PKG_BUILD_DIR); $(CP) mISDN.cfg.default standalone/mISDN.cfg )
endef

define Build/Compile
	( cd $(PKG_BUILD_DIR); $(MAKE) $(PKG_JOBS) modules \
		ARCH="$(LINUX_KARCH)" \
		CROSS_COMPILE="$(TARGET_CROSS)" \
		CC="$(TARGET_CC)" \
		CPP="$(TARGET_CC)" \
		LD="$(TARGET_CROSS)ld" \
		LINUX_SOURCE="$(LINUX_DIR)" \
		KR="$(LINUX_DIR)" )
endef

$(eval $(call KernelPackage,misdn-external))
