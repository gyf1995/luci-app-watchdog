include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-watchdog
PKG_VERSION:=1.0.6
PKG_RELEASE:=20250717

PKG_MAINTAINER:=sirpdboy  <herboy2008@gmail.com>
PKG_CONFIG_DEPENDS:=

LUCI_TITLE:=LuCI support for watchdog
LUCI_PKGARCH:=all
LUCI_DEPENDS:=+watchdog

# 关键行！！！
LUCI_NAME:=watchdog

include $(TOPDIR)/feeds/luci/luci.mk
