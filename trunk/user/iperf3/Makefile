include $(ROOTDIR)/rules.mk

PKG_NAME:=iperf
PKG_VERSION:=3.18

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://downloads.es.net/pub/iperf
PKG_HASH:=c0618175514331e766522500e20c94bfb293b4424eb27d7207fb427b88d20bab

PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

TARGET_CFLAGS += -D_GNU_SOURCE
CONFIGURE_ARGS += \
	--disable-shared \
	--enable-static \
	--without-openssl

$(eval $(call BuildPackage,iperf))

romfs:
	$(INSTALL_DIR) $(ROMFSDIR)/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/iperf3 $(ROMFSDIR)/bin/iperf3
