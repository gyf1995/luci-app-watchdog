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
	$(INSTALL_DIR) $(1)/usr/share/luci/luci-static/resources/view/watchdog
	$(CP) ./htdocs/luci-static/resources/view/watchdog/* $(1)/usr/share/luci/luci-static/resources/view/watchdog/

	# 安装json配置文件
	$(INSTALL_DIR) $(1)/usr/share/luci/luci-static/resources/view/watchdog
	$(INSTALL_DATA) ./root/usr/share/luci/www/watchdog.json $(1)/usr/share/luci/luci-static/resources/view/watchdog/watchdog.json

	# 安装中文翻译文件（OpenWrt构建系统会自动转换为.lmo）
	$(INSTALL_DIR) $(1)/usr/share/luci/i18n
	$(INSTALL_DATA) ./po/zh-cn/watchdog.po $(1)/usr/share/luci/i18n/luci-app-watchdog.zh-cn.po
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
