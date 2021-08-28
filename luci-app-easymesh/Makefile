# Copyright (C) 2021 Openwrt.org
#
# This is free software, licensed under the Apache License, Version 2.0 .
#

include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-easymesh
PKG_VERSION:=1.0
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=luci
  CATEGORY:=LuCI
  SUBMENU:=3. Applications
  DEPENDS:=+kmod-cfg80211 +batctl-default +kmod-batman-adv +wpad-mesh-openssl
  TITLE:=LuCI support for easymesh
  PKGARCH:=all
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/conffiles
/etc/config/easymesh
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/etc/init.d $(1)/etc/config $(1)/usr/lib/lua/luci $(1)/etc/uci-defaults
	$(CP) ./luasrc/* $(1)/usr/lib/lua/luci
	$(INSTALL_CONF) ./root/etc/config/easymesh $(1)/etc/config
	$(INSTALL_BIN) ./root/etc/init.d/easymesh $(1)/etc/init.d
	$(INSTALL_BIN) ./root/etc/uci-defaults/luci-app-easymesh $(1)/etc/uci-defaults/luci-app-easymesh
	$(INSTALL_DIR) $(1)/usr/share/rpcd/acl.d
	$(INSTALL_DATA) ./root/usr/share/rpcd/acl.d/*.json $(1)/usr/share/rpcd/acl.d/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))


