appfab_sources = [
  'main.c',
  'af-application.c',
  'af-window.c',
]

appfab_deps = [
  dependency('gtk4'),
  dependency('libadwaita-1', version: '>= 1.8'),
  dependency('libdex-1', version: '>= 1.0'),
  dependency('libfoundry-1', version: '>= 1.0'),
  dependency('libfoundry-gtk-1', version: '>= 1.0'),
  dependency('libfoundry-adw-1', version: '>= 1.0'),
]

blueprints = custom_target('blueprints',
  input: files(
    'shortcuts-dialog.blp',
    'af-window.blp',
  ),
  output: '.',
  command: [find_program('blueprint-compiler'), 'batch-compile', '@OUTPUT@', '@CURRENT_SOURCE_DIR@', '@INPUT@'],
)

appfab_sources += gnome.compile_resources('appfab-resources',
  'appfab.gresource.xml',
        c_name: 'appfab',
  dependencies: blueprints,
)

executable('appfab', appfab_sources,
  dependencies: appfab_deps,
       install: true,
)
