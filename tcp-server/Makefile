include $(TOPDIR)/rules.mk

PKG_NAME:=tcp-server
PKG_VERSION:=0.1.0
PKG_RELEASE:=0

# 
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=file:///home/kong/making/projects/repos/tcp-server.git
PKG_SOURCE_VERSION:=4ddfde9609422bfe3d6e90daee9da8bdd083d4a5

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=apps
  CATEGORY:=Applications
  TITLE:=A sample TCP server
  URL:=https://github.com/mlainani/applications
  MAINTAINER:= Madani Lainani <m.lainani@gmail.com>
endef

define Package/$(PKG_NAME)/description
  A sample TCP server
endef

TCP_SERVER_PATH:="$(PKG_BUILD_DIR)/target/aarch64-unknown-linux-musl/debug/tcp-server"

define Build/Compile
	(\
		cd $(PKG_BUILD_DIR) && \
		cargo build --target aarch64-unknown-linux-musl \
	)
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(TCP_SERVER_PATH) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/tcp-server.init $(1)/etc/init.d/tcp-server
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
