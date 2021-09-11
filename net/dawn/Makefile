#
# This software is licensed under the Public Domain.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=dawn
PKG_SOURCE_DATE:=2022-02-19
PKG_RELEASE:=$(AUTORELEASE)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/galeksandrp/DAWN.git
PKG_SOURCE_VERSION:=d2e5bd30813aa465851c0ba18ebe70cf45ff61ee
PKG_MIRROR_HASH:=skip

PKG_MAINTAINER:=Nick Hainke <vincent@systemli.org>
PKG_LICENSE:=GPL-2.0-only
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/dawn
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Decentralized wifi controller
  URL:=https://github.com/berlin-open-wireless-lab/DAWN.git
  DEPENDS:=$(DRV_DEPENDS) +libubus +libubox +libblobmsg-json +libuci +libgcrypt +libiwinfo +umdns
endef

define Package/dawn/description
  This package implements a decentralized wireless daemon.
endef

define Package/dawn/conffiles
/etc/config/dawn
endef

define Package/dawn/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/dawn $(1)/usr/sbin/dawn
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/dawn.init $(1)/etc/init.d/dawn
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/dawn.config $(1)/etc/config/dawn
endef

$(eval $(call BuildPackage,dawn))
