include $(ROOTDIR)/rules.mk

PKG_NAME:=naiveproxy
PKG_VERSION:=v131.0.6778.86-1

include $(INCLUDE_DIR)/package.mk

STATIC_FILE:=$(PKG_NAME)-v$(PKG_VERSION)-openwrt-mipsel_24kc-static.tar.xz
STATIC_SUBDIR:=$(PKG_NAME)-v$(PKG_VERSION)-openwrt-mipsel_24kc-static
define Download/$(PKG_NAME)-static
	URL:=https://github.com/klzgrad/naiveproxy/releases/download/v$(PKG_VERSION)
	URL_FILE:=$(STATIC_FILE)
	FILE:=$(STATIC_FILE)
	HASH:=ad1474d509e1ff39734eed28aa80db19ec4d2fc42d027fb8f11fff0332b06e49
endef

define Build/Prepare
	tar xf $(DL_DIR)/$(STATIC_FILE) -C $(PKG_BUILD_DIR)
endef

define Build/Configure
endef

define Build/Compile
	$(TARGET_CROSS)strip $(PKG_BUILD_DIR)/$(STATIC_SUBDIR)/naive
endef

$(eval $(call Download,$(PKG_NAME)-static))
$(eval $(call BuildPackage,naiveproxy))

romfs:
	$(INSTALL_DIR) $(ROMFSDIR)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(STATIC_SUBDIR)/naive $(ROMFSDIR)/usr/bin/naive
