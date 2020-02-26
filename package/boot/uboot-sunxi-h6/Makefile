#
# Copyright (C) 2013-2016 OpenWrt.org
# Copyright (C) 2017 Yousong Zhou
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_VERSION:=2020.01

PKG_HASH:=aa453c603208b1b27bd03525775a7f79b443adec577fdc6e8f06974025a135f1

PKG_MAINTAINER:=Icenowy Zheng <icenowy@aosc.io>

include $(INCLUDE_DIR)/u-boot.mk
include $(INCLUDE_DIR)/package.mk

define U-Boot/Default
  BUILD_TARGET:=sunxi
  UBOOT_IMAGE:=u-boot-sunxi-with-spl.bin
  UENV:=default
  HIDDEN:=1
endef

define U-Boot/pine_h64
  BUILD_SUBTARGET:=cortexa53
  NAME:=Pine H64
  BUILD_DEVICES:=pine64_pine-h64
  DEPENDS:=+PACKAGE_u-boot-pine_h64:arm-trusted-firmware-sunxi-h6
endef

UBOOT_TARGETS := \
	pine_h64

UBOOT_CONFIGURE_VARS += USE_PRIVATE_LIBGCC=yes

UBOOT_MAKE_FLAGS += \
	BL31=$(STAGING_DIR_IMAGE)/bl31_h6.bin

define Build/InstallDev
	$(INSTALL_DIR) $(STAGING_DIR_IMAGE)
	$(CP) $(PKG_BUILD_DIR)/$(UBOOT_IMAGE) $(STAGING_DIR_IMAGE)/$(BUILD_DEVICES)-u-boot-with-spl.bin
	mkimage -C none -A arm -T script -d uEnv-$(UENV).txt \
		$(STAGING_DIR_IMAGE)/$(BUILD_DEVICES)-boot.scr
endef

define Package/u-boot/install/default
endef

$(eval $(call BuildPackage/U-Boot))
