include $(TOPDIR)/rules.mk

PKG_NAME:=freifunk
PKG_VERSION:=1.0.0
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/freifunk

include $(INCLUDE_DIR)/package.mk

define Package/freifunk-basic
	SECTION:=base
	CATEGORY:=Freifunk
	DEFAULT:=y
	TITLE:= Freifunk-Bielefeld Basic
	URL:=http://freifunk-bielefeld.de
	DEPENDS:=+kmod-batman-adv +alfred +sockread\
		+uhttpd +haserl +uhttpd-mod-tls +px5g \
		+fastd +ip +odhcpd +simple-radvd \
		+ebtables +kmod-ebtables-ipv4 +kmod-ebtables-ipv6 \
		+haveged +autoupdater +simple-tc +@ATH_USER_REGD
endef

define Build/Prepare
	echo "all: " > $(PKG_BUILD_DIR)/Makefile
endef

define Package/freifunk-basic/install
	#nothing to do here
endef

define Package/freifunk/conffiles
	/etc/config/freifunk
endef

define Package/freifunk-debug
	SECTION:=base
	CATEGORY:=Freifunk
	DEFAULT:=n
	TITLE:=Freifunk-Bielefeld with debug tools
	DEPENDS:=+freifunk-basic \
		+@KMOD_BATMAN_ADV_DEBUG_LOG +iperf +tcpdump-mini
endef

$(eval $(call BuildPackage,freifunk-basic))
$(eval $(call BuildPackage,freifunk-debug))