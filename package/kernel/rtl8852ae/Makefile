include $(TOPDIR)/rules.mk

PKG_NAME:=rtl8852ae
PKG_RELEASE=1

PKG_LICENSE:=GPLv2
PKG_LICENSE_FILES:=

PKG_SOURCE_URL:=https://www.renew.sh/xosadmin/rtw89-opnew
PKG_MIRROR_HASH:=
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2021-08-11
PKG_SOURCE_VERSION:=1965eb9799b8872b587ce35e254c1367a1356c21

PKG_MAINTAINER:=Larry Finger <Larry.Finger@lwfinger.net>
PKG_BUILD_PARALLEL:=1
#PKG_EXTMOD_SUBDIRS:=rtl8852ae

STAMP_CONFIGURED_DEPENDS := $(STAGING_DIR)/usr/include/mac80211-backport/backport/autoconf.h

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/rtl8852ae
  SUBMENU:=Wireless Drivers
  TITLE:=Driver for Realtek 8852 AE devices
  DEPENDS:=+kmod-mac80211 +rtl8852ae-firmware +@DRIVER_11N_SUPPORT +@DRIVER_11AC_SUPPORT +@PCI_SUPPORT
  FILES:=\
        $(PKG_BUILD_DIR)/rtw89pci.ko \
        $(PKG_BUILD_DIR)/rtw89_core.ko
  AUTOLOAD:=$(call AutoProbe,rtw89_core)
  AUTOLOAD:=$(call AutoProbe,rtw89pci)
  PROVIDES:=kmod-rtl8852ae
endef

NOSTDINC_FLAGS := \
        $(KERNEL_NOSTDINC_FLAGS) \
        -I$(PKG_BUILD_DIR) \
        -I$(PKG_BUILD_DIR)/include \
        -I$(STAGING_DIR)/usr/include/mac80211-backport \
        -I$(STAGING_DIR)/usr/include/mac80211-backport/uapi \
        -I$(STAGING_DIR)/usr/include/mac80211 \
        -I$(STAGING_DIR)/usr/include/mac80211/uapi \
        -include backport/backport.h

NOSTDINC_FLAGS+=-DBUILD_OPENWRT

define Build/Compile
        +$(MAKE) $(PKG_JOBS) -C "$(LINUX_DIR)" \
                $(KERNEL_MAKE_FLAGS) \
                M="$(PKG_BUILD_DIR)" \
                NOSTDINC_FLAGS="$(NOSTDINC_FLAGS)" \
                modules
endef

$(eval $(call KernelPackage,rtl8852ae))
