include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-watchdog
PKG_VERSION:=1.0
PKG_RELEASE:=1

LUCI_TITLE:=iStoreOS Watchdog
LUCI_PKGARCH:=all
LUCI_DEPENDS:=+luci-base +luci-lib-ip +rpcd +luci-compat

PKG_MAINTAINER:=gyf1995

# 指定中文翻译目录
LUCI_LANG.zh-cn:=po/zh-cn

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

define Build/Compile
	true
endef

define Package/$(PKG_NAME)/install
	# 安装网页静态资源
	$(INSTALL_DIR) $(1)/www/luci-static/resources/view/watchdog
	$(CP) ./htdocs/luci-static/resources/view/watchdog/* $(1)/www/luci-static/resources/view/watchdog/

	# 安装菜单 json 配置
	$(INSTALL_DIR) $(1)/usr/share/luci/menu.d
	$(INSTALL_DATA) ./root/usr/share/luci/menu.d/luci-app-watchdog.json $(1)/usr/share/luci/menu.d/

	# 安装 rpcd acl json 配置
	$(INSTALL_DIR) $(1)/usr/share/rpcd/acl.d
	$(INSTALL_DATA) ./root/usr/share/rpcd/acl.d/luci-app-watchdog.json $(1)/usr/share/rpcd/acl.d/

	# 安装 watchdog api 目录
	$(INSTALL_DIR) $(1)/usr/share/watchdog/api
	$(CP) ./root/usr/share/watchdog/api/* $(1)/usr/share/watchdog/api/

	# 安装中文翻译文件
	$(INSTALL_DIR) $(1)/usr/share/luci/i18n
	$(INSTALL_DATA) ./po/zh-cn/watchdog.po $(1)/usr/share/luci/i18n/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
