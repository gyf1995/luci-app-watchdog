include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-watchdog
PKG_VERSION:=1.0
PKG_RELEASE:=1

LUCI_TITLE:=LuCI Support for Watchdog
LUCI_DEPENDS:=+luci-base
LUCI_PKGARCH:=all

include $(TOPDIR)/feeds/luci/luci.mk

# LMO 编译支持
define Build/Prepare
	$(call Build/Prepare/Default)
	po2lmo ./po/zh-cn/watchdog.po $(PKG_BUILD_DIR)/watchdog.zh-cn.lmo
endef

define Package/$(PKG_NAME)/install
	$(call Package/luci/install/template,$(1))

	# 菜单
	$(INSTALL_DIR) $(1)/usr/share/luci/menu.d
	$(INSTALL_DATA) ./root/usr/share/luci/menu.d/luci-app-watchdog.json $(1)/usr/share/luci/menu.d/

	# ACL
	$(INSTALL_DIR) $(1)/usr/share/rpcd/acl.d
	$(INSTALL_DATA) ./root/usr/share/rpcd/acl.d/luci-app-watchdog.json $(1)/usr/share/rpcd/acl.d/

	# API
	$(INSTALL_DIR) $(1)/usr/share/watchdog/api
	cp -fpR ./root/usr/share/watchdog/api/* $(1)/usr/share/watchdog/api/

	# LMO 翻译
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/i18n
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/watchdog.zh-cn.lmo $(1)/usr/lib/lua/luci/i18n/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
