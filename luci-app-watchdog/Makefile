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

# 调用 OpenWrt 构建系统
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

# 安装文件
define Build/Compile
  true
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/controller
	$(INSTALL_DATA) ./root/usr/lib/lua/luci/controller/watchdog.lua $(1)/usr/lib/lua/luci/controller/watchdog.lua
	
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/model/cbi
	$(INSTALL_DATA) ./root/usr/lib/lua/luci/model/cbi/watchdog.lua $(1)/usr/lib/lua/luci/model/cbi/watchdog.lua

	$(INSTALL_DIR) $(1)/usr/share/luci/i18n
	$(INSTALL_DATA) ./po/zh-cn/luci-app-watchdog.zh-cn.po $(1)/usr/share/luci/i18n/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
