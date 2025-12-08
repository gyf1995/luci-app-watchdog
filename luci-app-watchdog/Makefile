include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-watchdog
PKG_VERSION:=1.0
PKG_RELEASE:=1

LUCI_TITLE:=iStoreOS Watchdog
LUCI_PKGARCH:=all

LUCI_DEPENDS:=+luci-base +luci-lib-ip +rpcd +luci-compat

PKG_MAINTAINER:=gyf1995

include $(TOPDIR)/feeds/luci/luci.mk

PO2LMO:=po2lmo

define Package/$(PKG_NAME)/install
	# 安装菜单 JSON 和其它资源
	$(INSTALL_DIR) $(1)/usr/share/luci/menu.d
	$(INSTALL_DATA) ./root/usr/share/luci/menu.d/luci-app-watchdog.json $(1)/usr/share/luci/menu.d/

	$(INSTALL_DIR) $(1)/usr/share/rpcd/acl.d
	$(INSTALL_DATA) ./root/usr/share/rpcd/acl.d/luci-app-watchdog.json $(1)/usr/share/rpcd/acl.d/

	$(INSTALL_DIR) $(1)/usr/share/watchdog/api
	$(INSTALL_DATA) ./root/usr/share/watchdog/api/* $(1)/usr/share/watchdog/api/

	# 创建语言目录
	$(INSTALL_DIR) $(1)/usr/share/luci/i18n

	# 编译并安装 lmo 文件（中文）
	for po in $(PKG_BUILD_DIR)/po/zh-cn/*.po; do \
		$(PO2LMO) $$po $(1)/usr/share/luci/i18n/$$(basename $${po%.po}).lmo; \
	done
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
