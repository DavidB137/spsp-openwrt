include $(TOPDIR)/rules.mk

PKG_NAME:=spsp
PKG_VERSION:=0.4.1
PKG_RELEASE:=1

PKG_MAINTAINER:=David Benko <davidbenko@davidbenko.dev>
PKG_LICENSE:=Apache-2.0

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/DavidB137/spsp.git
PKG_SOURCE_DATE:=2024-03-17
PKG_SOURCE_VERSION:=816f4819234f777789b13320c5ff55200e954b1f
PKG_MIRROR_HASH:=eed30a22c178806f96791915f6a15462217c4e11d16808a870fdd6bd133b9d62
PKG_BUILD_DIR:=$(BUILD_DIR)/spsp-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

MAKE_PATH:=linux
CMAKE_SOURCE_SUBDIR:=$(MAKE_PATH)
CMAKE_INSTALL:=1
CMAKE_OPTIONS += \
	-DSPSP_LOG_NO_COLORS=TRUE

define Package/libspsp
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=IoT
	TITLE:=Simple publish subscribe protocol library
	URL:=https://github.com/DavidB137/spsp
	DEPENDS:=+libstdcpp +libpthread +libpaho-mqtt3as
endef

define Package/libspsp/description
	Simple publish subscribe protocol (SPSP) library.
	Used by packages like `spsp-bridge-espnow`.
endef

define Package/spsp-bridge-espnow
	SECTION:=net
	CATEGORY:=Network
	SUBMENU:=Wireless
	TITLE:=SPSP ESP-NOW bridge
	URL:=https://github.com/DavidB137/spsp
	DEPENDS:=+libstdcpp +libpthread +libspsp
endef

define Package/spsp-bridge-espnow/description
	Bridge of simple publish subscribe protocol (SPSP) utilizing ESP-NOW
	as local layer protocol.
endef

define Package/libspsp/install
	$(INSTALL_DIR) $(1)/etc/config $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libspsp.so* $(1)/usr/lib/
	$(INSTALL_CONF) ./files/spsp.config $(1)/etc/config/spsp
endef

define Package/spsp-bridge-espnow/install
	$(INSTALL_DIR) $(1)/etc/init.d $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/spsp_bridge_espnow $(1)/usr/bin/
	$(INSTALL_BIN) ./files/spsp_bridge_espnow.init $(1)/etc/init.d/spsp_bridge_espnow
endef

$(eval $(call BuildPackage,libspsp))
$(eval $(call BuildPackage,spsp-bridge-espnow))
