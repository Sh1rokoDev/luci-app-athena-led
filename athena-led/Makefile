include $(TOPDIR)/rules.mk

PKG_NAME:=athena-led
PKG_VERSION:=1.0.0
PKG_RELEASE:=1

PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Sh1roko233 <https://github.com/Sh1rokoDev>
PKG_BUILD_DEPENDS:=rust/host
PKG_BUILD_PARALLEL:=1
PKG_BUILD_FLAGS:=no-lto

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/rust/rust-package.mk

define Package/athena-led
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=JDCloud AX6600 (Athena) LED matrix screen daemon
  DEPENDS:=$(RUST_ARCH_DEPENDS)
  URL:=https://github.com/Sh1rokoDev/athena-led
endef

define Package/athena-led/description
  Rust daemon driving the JDCloud AX6600 (Athena) LED matrix screen,
  including per-interface upload/download speed display modes.
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src $(PKG_BUILD_DIR)/
	$(CP) ./Cargo.toml ./Cargo.lock ./LICENSE $(PKG_BUILD_DIR)/
endef

define Package/athena-led/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/bin/athena-led $(1)/usr/sbin/athena-led
endef

$(eval $(call BuildPackage,athena-led))
