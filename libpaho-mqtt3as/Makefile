include $(TOPDIR)/rules.mk

PKG_NAME:=libpaho-mqtt3as
PKG_VERSION:=1.3.13
PKG_RELEASE:=1

PKG_MAINTAINER:=David Benko <davidbenko@davidbenko.dev>
PKG_LICENSE:=EPL-2.0

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/eclipse/paho.mqtt.c.git
PKG_SOURCE_DATE:=2023-10-13
PKG_SOURCE_VERSION:=07a875788d8cc6f5833b12581d6e3e349b34d719
PKG_MIRROR_HASH:=a199ff9c6a7f900fa63e2f326630af6cc802907826e345bfa9d2c8d553283f11
PKG_BUILD_DIR:=$(BUILD_DIR)/libpaho-mqtt3as-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_INSTALL:=1
CMAKE_OPTIONS += \
	-DPAHO_WITH_SSL=TRUE \
	-DPAHO_ENABLE_TESTING=FALSE \
	-DPAHO_BUILD_SAMPLES=FALSE

define Package/libpaho-mqtt3as
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=Paho MQTT C library - async, TLS
	URL:=https://eclipse.org/paho
	DEPENDS:=+libc +libpthread +libopenssl
endef

define Package/libpaho-mqtt3as/description
	Paho MQTT C library - asynchronous variant with TLS support.
endef

define Package/libpaho-mqtt3as/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/src/libpaho-mqtt3as.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libpaho-mqtt3as))

