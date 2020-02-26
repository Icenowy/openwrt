#
# Copyright (C) 2017 Hauke Mehrtens
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=arm-trusted-firmware-sunxi-h6
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/ARM-software/arm-trusted-firmware
PKG_SOURCE_DATE:=2019-10-22
PKG_SOURCE_VERSION:=a04808c16cfc126d9fe572ae7c4b5a3d39de5796

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=license.md

PKG_MAINTAINER:=Icenowy Zheng <icenowy@aosc.io>

include $(INCLUDE_DIR)/package.mk


define Package/arm-trusted-firmware-sunxi-h6
    SECTION:=boot
    CATEGORY:=Boot Loaders
    TITLE:=ARM Trusted Firmware for Allwinner H6
    DEPENDS:=@TARGET_sunxi_cortexa53
endef

export GCC_HONOUR_COPTS=s

MAKE_VARS = \
	CROSS_COMPILE="$(TARGET_CROSS)"

MAKE_FLAGS += \
	PLAT=sun50i_h6 \
	bl31

define Build/InstallDev
	$(INSTALL_DIR) $(STAGING_DIR_IMAGE)
	$(CP) $(PKG_BUILD_DIR)/build/sun50i_h6/release/bl31.bin $(STAGING_DIR_IMAGE)/bl31_h6.bin
endef

define Package/arm-trusted-firmware-sunxi-h6/install
endef

$(eval $(call BuildPackage,arm-trusted-firmware-sunxi-h6))
