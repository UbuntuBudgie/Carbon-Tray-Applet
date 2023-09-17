subdir('carbontray')

applet_tray_sources = ['CarbonTrayApplet.vala', applet_tray_resources]

applet_tray_deps = [
    budgie_dep,
    dep_gtk3,
    dependency('x11'),
    dependency('gdk-x11-3.0'),
    peas_dep,
    link_libcarbontray,
]

shared_library(
    'carbontrayapplet',
    applet_tray_sources,
    dependencies: applet_tray_deps,
    vala_args: [
        '--pkg', 'libpeas-1.0',
        join_paths(meson.project_source_root(), 'src', 'carbontray', 'carbontray-1.0.vapi'),
    ],
    install: true,
    install_dir: applet_tray_dir,
)

custom_target('plugin-file-tray',
    input : 'CarbonTrayApplet.plugin.in',
    output : 'CarbonTrayApplet.plugin',
    command : [intltool, '--desktop-style', podir, '@INPUT@', '@OUTPUT@'],
    install : true,
    install_dir : applet_tray_dir)
