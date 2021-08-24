#
# Copyright (C) 2021 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=rtl8852ae-firmware
PKG_SOURCE_DATE:=2021-07-24
PKG_SOURCE_VERSION:=bf0061dac76be30c6342863128e734893e33aaae
PKG_MIRROR_HASH:=9284e367087e9cf8a212f4e5837fdd85f4baf66a4cc7c0b15e512b438501fe18
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://www.renew.sh/xosadmin/rtw89.git

PKG_MAINTAINER:=Larry Finger <Larry.Finger@lwfinger.net>

include $(INCLUDE_DIR)/package.mk

define Package/rtl8852ae-firmware
	SECTION:=firmware
	CATEGORY:=Firmware
	TITLE:=Firmware for Realtek 8852 AE devices
endef

define Build/Compile

endef

define Package/rtl8852ae-firmware/install
	$(INSTALL_DIR) $(1)/lib/firmware/rtw89
	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/rtw8852a_fw.bin \
		$(1)/lib/firmware/rtw89/
endef

$(eval $(call BuildPackage,rtl8852ae-firmware))
