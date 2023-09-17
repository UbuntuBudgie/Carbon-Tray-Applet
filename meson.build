project('carbon-tray',
	['vala', 'c'],
	version: '1.0',
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

#applet_tray_dir = applets_dir + '.tray'

subdir('data')
subdir('src')

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