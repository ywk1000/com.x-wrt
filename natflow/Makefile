#
# Copyright (C) 2017-2019 Chen Minqiang <ptpt52@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=natflow
PKG_VERSION:=0.0.1
PKG_RELEASE:=65b18b426bf368dbb6195165800806be0eee2f60

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_RELEASE).tar.xz
PKG_SOURCE_URL:=https://github.com/ptpt52/natflow.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_RELEASE)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_MAINTAINER:=Chen Minqiang <ptpt52@gmail.com>
PKG_LICENSE:=GPL-2.0

include $(INCLUDE_DIR)/package.mk

define KernelPackage/natflow
  CATEGORY:=X
  SUBMENU:=Fast Forward Stacks
  TITLE:=natflow kernel driver
  FILES:=$(PKG_BUILD_DIR)/natflow.ko
  KCONFIG:=
  AUTOLOAD:=$(call AutoLoad,96,natflow)
  DEPENDS:= +kmod-ipt-conntrack +kmod-ipt-nat +kmod-ipt-ipset
endef

define KernelPackage/natflow/description
  fast nat forward kmod
endef

include $(INCLUDE_DIR)/kernel-defaults.mk

define Build/Compile/natflow
	$(MAKE) $(KERNEL_MAKEOPTS) SUBDIRS="$(PKG_BUILD_DIR)" modules
endef

define Build/Compile
	$(call Build/Compile/natflow)
endef

$(eval $(call KernelPackage,natflow))
