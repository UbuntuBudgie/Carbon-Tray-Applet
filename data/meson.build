gresource = join_paths(meson.current_source_dir(), 'plugin.gresource.xml')

applet_tray_resources = gnome.compile_resources(
    'tray-applet-resources',
    gresource,
    source_dir: meson.current_source_dir(),
    c_name: 'budgie_tray',
)
