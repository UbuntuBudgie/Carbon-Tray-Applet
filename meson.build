project('carbon-tray',
	['vala', 'c'],
	version: '0.1',
	meson_version: '>= 0.60.0'
)


add_project_arguments([
    '-DGETTEXT_PACKAGE="@0@"'.format(meson.project_name())
],
    language: 'c',
)

dep_gtk3 = dependency('gtk+-3.0')
gnome = import('gnome')
prefix = get_option('prefix')
libdir = join_paths(prefix, get_option('libdir'))
datadir = join_paths(prefix, get_option('datadir'))
applet_tray_dir = join_paths(libdir, 'budgie-desktop', 'plugins', 'carbon-tray')
intltool = find_program('intltool-merge')
podir = join_paths(meson.project_source_root(), 'po')
budgie_dep = dependency('budgie-1.0')
peas_dep = dependency('libpeas-gtk-1.0')
i18n = import('i18n')


subdir('carbontray')

#applet_tray_dir = applets_dir + '.tray'

custom_target('plugin-file-tray',
    input : 'CarbonTrayApplet.plugin.in',
    output : 'CarbonTrayApplet.plugin',
    command : [intltool, '--desktop-style', podir, '@INPUT@', '@OUTPUT@'],
    install : true,
    install_dir : applet_tray_dir)

subdir('data')

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
        join_paths(meson.project_source_root(), 'carbontray', 'carbontray-1.0.vapi'),
    ],
    install: true,
    install_dir: applet_tray_dir,
)

install_data(
    'schema/org.ubuntubudgie.plugins.tray.gschema.xml',
    install_dir: join_paths(datadir, 'glib-2.0', 'schemas'),
)

#gnome.compile_schemas(build_by_default: true, 
#    depend_files: 'schema/org.ubuntubudgie.plugins.tray.gschema.xml')

#gnome.post_install(
#			glib_compile_schemas: true,
#			gtk_update_icon_cache: true,
#			update_desktop_database: true
#		)

gnome.post_install(
			glib_compile_schemas: true
		)