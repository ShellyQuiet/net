include $(TOPDIR)/rules.mk

PKG_NAME:=sing-box
PKG_VERSION:=1.10.0
PKG_RELEASE:=1

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/SagerNet/sing-box/tar.gz/refs/tags
PKG_HASH:=eb7af91189122bcb748912e205cdddb8b434c69bea67cfbe1a4082a577380814

PKG_LICENSE:=GPL-3.0-or-later
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1

GO_PKG:=github.com/SagerNet/sing-box
GO_PKG_BUILD_PKG:=./cmd/sing-box

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/sing-box
  SECTION:=net
  CATEGORY:=Network
  TITLE:=sing-box universal proxy platform
  URL:=https://sing-box.sagernet.org
  DEPENDS:=$(GO_ARCH_DEPENDS) +ca-bundle +ip-full +kmod-tun
endef

define Package/sing-box/conffiles
/etc/sing-box/config.json
endef

define Build/Compile
  $(call GoPackage/Build/Compile)
endef

define Package/sing-box/install
  $(call GoPackage/Package/Install/Bin,$(1))
  $(INSTALL_DIR) $(1)/etc/sing-box
  $(INSTALL_DIR) $(1)/etc/init.d
  $(INSTALL_BIN) ./files/sing-box.init $(1)/etc/init.d/sing-box
endef

$(eval $(call GoBinPackage,sing-box))
$(eval $(call BuildPackage,sing-box))
