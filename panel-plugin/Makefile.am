
AM_CPPFLAGS = \
	-I$(top_srcdir) \
	-DG_LOG_DOMAIN=\"pulseaudio-plugin\" \
	-DPACKAGE_LOCALE_DIR=\"$(localedir)\" \
	-DDEFAULT_MIXER_COMMAND=\"$(DEFAULT_MIXER_COMMAND)\" \
	-DDATADIR=\""$(datadir)"\" \
	$(PLATFORM_CPPFLAGS)

#
# PulseAudio plugin
#
plugindir = \
	$(libdir)/xfce4/panel/plugins

plugin_LTLIBRARIES = \
	libpulseaudio-plugin.la

libpulseaudio_built_sources = \
	pulseaudio-dialog_ui.h

libpulseaudio_plugin_la_SOURCES = \
	$(libpulseaudio_built_sources) \
	pulseaudio-debug.c \
	pulseaudio-debug.h \
	pulseaudio-volume.c \
	pulseaudio-volume.h \
	pulseaudio-button.c \
	pulseaudio-button.h \
	pulseaudio-config.c \
	pulseaudio-config.h \
	pulseaudio-plugin.c \
	pulseaudio-plugin.h \
	pulseaudio-dialog.c \
	pulseaudio-dialog.h \
	pulseaudio-menu.c \
	pulseaudio-menu.h \
	pulseaudio-mpris.c \
	pulseaudio-mpris.h \
	pulseaudio-mpris-player.c \
	pulseaudio-mpris-player.h \
	pulseaudio-notify.c \
	pulseaudio-notify.h \
	scalemenuitem.c \
	scalemenuitem.h \
	mprismenuitem.c \
	mprismenuitem.h \
	devicemenuitem.c \
	devicemenuitem.h


libpulseaudio_plugin_la_CFLAGS = \
	$(PULSEAUDIO_CFLAGS) \
	$(GLIB_CFLAGS) \
	$(GIO_CFLAGS) \
	$(GIO_UNIX_CFLAGS) \
	$(GTK_CFLAGS) \
	$(LIBXFCE4UTIL_CFLAGS) \
	$(LIBXFCE4UI_CFLAGS) \
	$(LIBXFCE4PANEL_CFLAGS) \
	$(XFCONF_CFLAGS) \
	$(KEYBINDER_CFLAGS) \
	$(LIBNOTIFY_CFLAGS) \
	$(LIBCANBERRA_CFLAGS) \
	$(EXO_CFLAGS) \
	$(WNCK_CFLAGS) \
	$(LIBXFCE4WINDOWING_CFLAGS) \
	$(PLATFORM_CFLAGS)

libpulseaudio_plugin_la_LDFLAGS = \
	-avoid-version \
	-module \
	-no-undefined \
	-export-symbols-regex '^xfce_panel_module_(preinit|init|construct)' \
	$(PLATFORM_LDFLAGS)

libpulseaudio_plugin_la_LIBADD = \
	$(PULSEAUDIO_LIBS) \
	$(GLIB_LIBS) \
	$(GIO_LIBS) \
	$(GIO_UNIX_LIBS) \
	$(GTK_LIBS) \
	$(LIBXFCE4UTIL_LIBS) \
	$(LIBXFCE4UI_LIBS) \
	$(LIBXFCE4PANEL_LIBS) \
	$(XFCONF_LIBS) \
	$(KEYBINDER_LIBS) \
	$(LIBNOTIFY_LIBS) \
	$(LIBCANBERRA_LIBS) \
	$(EXO_LIBS) \
	$(WNCK_LIBS) \
	$(LIBXFCE4WINDOWING_LIBS) \
	$(LIBM)

#
# Desktop file
#
desktopdir = \
	$(datadir)/xfce4/panel/plugins

desktop_in_files = \
	pulseaudio.desktop.in

desktop_in_in_files = $(desktop_in_files:.desktop.in=.desktop.in.in)
desktop_DATA = $(desktop_in_files:.desktop.in=.desktop)

$(desktop_DATA): $(desktop_in_files) Makefile
	$(AM_V_GEN)$(MSGFMT) --desktop --template $< -d $(top_srcdir)/po -o $@

EXTRA_DIST = \
	pulseaudio-dialog.glade \
	$(desktop_in_in_files)

DISTCLEANFILES = \
	$(desktop_in_files) \
	$(desktop_DATA)

if MAINTAINER_MODE
BUILT_SOURCES = \
	$(libpulseaudio_built_sources)

DISTCLEANFILES += \
	$(libpulseaudio_built_sources)

pulseaudio-dialog_ui.h: pulseaudio-dialog.glade
	$(AM_V_GEN) xdt-csource --static --strip-comments --strip-content --name=pulseaudio_dialog_ui $< >$@
endif

# vi:set ts=8 sw=8 noet ai nocindent syntax=automake:
