include $(TOPDIR)/rules.mk

PKG_NAME:=plugin_gargoyle_theme_flat_blue
PKG_VERSION:=$(GARGOYLE_VERSION)
ifeq ($(GARGOYLE_VERSION),)
     PKG_VERSION:=1.0.0
endif
PKG_RELEASE:=1


PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/plugin-gargoyle-theme-flat-blue
	SECTION:=admin
	CATEGORY:=Administration
	SUBMENU:=Gargoyle Web Interface
	TITLE:=Flat Blue Theme
	MAINTAINER:=Michael Gray <support@lantisproject.com>
	PKGARCH:=all
endef

define Package/plugin-gargoyle-theme-flat-blue/description
	Flat blue theme for Gargoyle
endef

define Build/Prepare
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/plugin-gargoyle-theme-flat-blue/install
	$(INSTALL_DIR) $(1)
	$(CP) ./files/* $(1)/
endef

define Package/plugin-gargoyle-theme-flat-blue/postinst
	if [ -z "$${IPKG_INSTROOT}" ] ; then 
		/etc/init.d/gargoyle_themes restart 
	fi 
endef
define Package/plugin-gargoyle-theme-flat-blue/postrm
	if [ -z "$${IPKG_INSTROOT}" ] ; then 
		IFS=$$(echo -en "\n\b") 
		for d in `find /www/themes/ -type d` ; do 
			if [ -d "$$d" ] ; then 
				contents=$$(ls "$$d") 
				if [ -z "$$contents" ] ; then 
					rmdir -p "$$d" 2>/dev/null 
				fi 
			fi 
		done 
		/etc/init.d/gargoyle_themes restart 
	fi 
endef


$(eval $(call BuildPackage,plugin-gargoyle-theme-flat-blue))
