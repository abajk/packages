include $(TOPDIR)/rules.mk

PKG_NAME:=pci_debug
PKG_VERSION:=1.0
PKG_RELEASE:=2

PKG_SOURCE:=pcie_debug-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/Martoni/pcie_debug/archive/refs/tags/$(PKG_VERSION)?
PKG_HASH:=3cbcdc58cc717d786cb775adf04dde2eaf96c93467eeb8a022e6cda5c7c6af46

PKG_MAINTAINER:=Aleksander Jan Bajkowski <olek2@wp.pl>
PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/pci-debug
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=PCIe Debug Tool
  URL:=https://github.com/Martoni/pcie_debug
endef

define Package/pci-debug/description
	Command line tool to Read/Write to PCIe BARx memory space
endef

define Build/Configure
	# Failed configure.sh leaves stub config.h around.
	rm -f $(PKG_BUILD_DIR)/config.h
	( cd $(PKG_BUILD_DIR); yes $$$$'\n' | ./configure.sh config.in )
endef

define Package/pci-debug/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mii-tool $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,pci-debug))
