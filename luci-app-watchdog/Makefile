include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-watchdog
PKG_VERSION:=1.0
PKG_RELEASE:=1

LUCI_TITLE:=iStoreOS Watchdog
LUCI_PKGARCH:=all
LUCI_DEPENDS:=+luci-base +luci-lib-ip +rpcd +luci-compat

PKG_MAINTAINER:=gyf1995

include $(TOPDIR)/feeds/luci/luci.mk

define Package/$(PKG_NAME)
  SECTION:=luci
  CATEGORY:=LuCI
  SUBMENU:=3. Applications
  TITLE:=$(LUCI_TITLE)
  DEPENDS:=$(LUCI_DEPENDS)
  MAINTAINER:=$(PKG_MAINTAINER)
  PKGARCH:=$(LUCI_PKGARCH)
endef

define Package/$(PKG_NAME)/description
  iStoreOS Watchdog LuCI Application with Chinese localization support.
endef


# ================== 构建 .lmo ==================

define Build/Prepare
	po2lmo ./po/zh-cn/watchdog.po ./po/zh-cn/watchdog.zh-cn.lmo
endef

define Build/Compile
	true
endef

# ================== 安装文件 ==================

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/share/luci/luci-static/resources/view/watchdog
	$(CP) ./htdocs/luci-static/resources/view/watchdog/* $(1)/usr/share/luci/luci-static/resources/view/watchdog/

	$(INSTALL_DIR) $(1)/usr/share/luci/menu.d
	$(INSTALL_DATA) ./root/usr/share/luci/menu.d/luci-app-watchdog.json $(1)/usr/share/luci/menu.d/

	$(INSTALL_DIR) $(1)/usr/share/rpcd/acl.d
	$(INSTALL_DATA) ./root/usr/share/rpcd/acl.d/luci-app-watchdog.json $(1)/usr/share/rpcd/acl.d/

	$(INSTALL_DIR) $(1)/usr/share/watchdog/api
	$(CP) ./root/usr/share/watchdog/api/* $(1)/usr/share/watchdog/api/

	# 安装翻译文件
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/i18n
	$(INSTALL_DATA) ./po/zh-cn/watchdog.zh-cn.lmo $(1)/usr/lib/lua/luci/i18n/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
