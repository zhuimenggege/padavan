include $(ROOTDIR)/rules.mk

PKG_NAME:=sing-box
PKG_VERSION:=1.10.5

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/SagerNet/sing-box/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=ca0385b45d160c2c2a1d0e09665f4f04caac27cb3dd9d6132173316dfd873b75

include $(INCLUDE_DIR)/package.mk

define Build/Configure
endef

define Build/Compile
	(cd $(PKG_BUILD_DIR); \
		GOOS=linux GOARCH=mipsle CGO_ENABLED=0 \
		go build -v -trimpath -tags "with_gvisor,with_quic,with_utls,with_wireguard,with_clash_api" \
		-ldflags "-X 'github.com/sagernet/sing-box/constant.Version=$(PKG_VERSION)' -s -w -buildid=" \
		./cmd/sing-box; \
	)
endef

$(eval $(call BuildPackage,sing-box))

romfs:
	$(INSTALL_DIR) $(ROMFSDIR)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/sing-box $(ROMFSDIR)/usr/bin/sing-box
