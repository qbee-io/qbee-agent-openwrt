include $(TOPDIR)/rules.mk

PKG_NAME:=qbee-agent
PKG_VERSION:=2024.23
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE
PKG_RELEASE:=1
PKG_GIT_COMMIT:=3219c17730eab4c80598494732b4bed4c4c18b51

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_GIT_URL:=github.com/qbee-io/qbee-agent
PKG_GIT_REF:=$(PKG_VERSION)
PKG_SOURCE_URL:=https://$(PKG_GIT_URL)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_MAINTAINER:=Jon Henrik Bjørnstad <jonhenrik@qbee.io>

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_BUILD_FLAGS:=no-mips16
PKG_USE_MIPS16:=0

GO_PKG:=go.qbee.io/agent
GO_PKG_LDFLAGS:=-X go.qbee.io/agent/app.Version=$(PKG_VERSION) \
	-X go.qbee.io/agent/app.Commit=$(PKG_GIT_COMMIT)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/qbee-agent
	SECTION:=admin
	CATEGORY:=Administration
	TITLE:=qbee.io fleet management agent
endef

define Package/qbee-agent/description
	qbee.io is a SaaS provided fleet management solution. This package provides the agent
	that runs on the device and communicates with the qbee.io server.
	
	https://qbee.io
endef

define Package/qbee-agent/install
	$(INSTALL_DIR) $(1)/etc/qbee/ppkeys
	$(INSTALL_CONF) $(PKG_BUILD_DIR)/package/share/ssl/ca.cert $(1)/etc/qbee/ppkeys/ca.cert

	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(GO_PKG_BUILD_BIN_DIR)/agent $(1)/usr/bin/qbee-agent

	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/qbee-agent.init $(1)/etc/init.d/qbee-agent
endef

$(eval $(call BuildPackage,qbee-agent))
