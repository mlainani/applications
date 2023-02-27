include $(TOPDIR)/rules.mk

PKG_NAME:=lwm2m-client
PKG_VERSION:=0.1.0
PKG_RELEASE:=0

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=file:///home/kong/making/projects/repos/lwm2m-client.git
PKG_SOURCE_VERSION:=692e435aef9f8fb396464a2477092481bde037eb

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=apps
  CATEGORY:=Applications
  TITLE:=A sample LwM2M client
  URL:=https://github.com/mlainani/applications
  MAINTAINER:= Madani Lainani <m.lainani@gmail.com>
endef

define Package/$(PKG_NAME)/description
  A sample LwM2M client
endef

LWM2M_CLIENT_PATH:="$(PKG_BUILD_DIR)/target/aarch64-unknown-linux-musl/debug/lwm2m-client"

define Build/Compile
	(\
		cd $(PKG_BUILD_DIR) && \
		cargo build --target aarch64-unknown-linux-musl \
	)
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(LWM2M_CLIENT_PATH) $(1)/usr/bin
endef

$(eval $(call BuildPackage,$(PKG_NAME)))