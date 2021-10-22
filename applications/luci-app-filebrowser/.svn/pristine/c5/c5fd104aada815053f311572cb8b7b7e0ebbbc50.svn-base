# Copyright (C) 2016 Openwrt.org
#
# This is free software, licensed under the Apache License, Version 2.0 .
#
# Improve by guyezi <admin@guyezi.com>
#

include $(TOPDIR)/rules.mk

LUCI_TITLE:=LuCI Support for FileBrowser
LUCI_DEPENDS:=+filebrowser +luci
LUCI_PKGARCH:=all

PKG_NAME:=luci-app-filebrowser
PKG_VERSION:=3.0
PKG_RELEASE:=1

PKG_LICENSE:=GPLv3
PKG_MAINTAINER:=[CTCGFW] Project OpenWRT

PO2LMO:=$(BUILD_DIR)/luci/build/po2lmo

define Build/Prepare
	$(foreach po,$(wildcard ${CURDIR}/po/*/*.po), \
		$(PO2LMO) $(po) $(PKG_BUILD_DIR)/$(patsubst %.po,%.lmo,$(notdir $(po)));)
endef

include $(TOPDIR)/feeds/luci/luci.mk

# call BuildPackage - OpenWrt buildroot signature
