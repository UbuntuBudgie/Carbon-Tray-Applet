# Carbon-Tray-Applet
Budgie Applet that displays GtkStatusIcon (xembed) icons.  This applet is only applicable for budgie-desktop v10.8 and later.

Original source from github.com/buddiesofbudgie/budgie-desktop forked at v10.7.2

<img src="./screenshots/nemo-carbon.png"/>

This applet supports legacy applications that currently do not have StatusNotifier / AppIndicator support.  These apps will no longer display panel icons in a future budgie desktop where Wayland will be the default.

We encourage everyone to help update these legacy applications to display panel icons with a more modern display protocol such as StatusNotifier.

xembed icons also do not scale and will look out of place on a modern budgie panel.

## Dependencies

- meson (>=0.60)
- ninja
- libpeas-1.0
- libpeas-gtk-1.0
- x11
- gdk-x11-3.0
- gtk+-3.0
- gnome
- intltool-merge
- i18n
- budgie-1.0
