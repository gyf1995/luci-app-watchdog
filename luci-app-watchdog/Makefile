include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-watchdog
PKG_VERSION:=1.0
PKG_RELEASE:=1

LUCI_TITLE:=iStoreOS Watchdog
LUCI_PKGARCH:=all

LUCI_DEPENDS:=+luci-base +luci-lib-ip +rpcd +luci-compat

PKG_MAINTAINER:=gyf1995

include $(TOPDIR)/feeds/luci/luci.mk

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/share/luci/i18n
	for po in $(PKG_BUILD_DIR)/po/zh-cn/*.po; do \
		po2lmo $$po $(1)/usr/share/luci/i18n/$$(basename $$po .po).zh-cn.lmo; \
	done

	$(INSTALL_DIR) $(1)/usr/lib/lua/luci
	cp -r ./luasrc/* $(1)/usr/lib/lua/luci/
endef

# call BuildPackage - OpenWrt build system
$(eval $(call BuildPackage,$(PKG_NAME)))
