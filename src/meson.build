pkgdatadir = get_option('prefix') / get_option('datadir') / meson.project_name()
moduledir = pkgdatadir / 'photo_transfer_wizard'
gnome = import('gnome')

gnome.compile_resources('photo-transfer-wizard',
  'photo-transfer-wizard.gresource.xml',
  gresource_bundle: true,
  install: true,
  install_dir: pkgdatadir,
)

python = import('python')

conf = configuration_data()
conf.set('PYTHON', python.find_installation('python3').full_path())
conf.set('VERSION', meson.project_version())
conf.set('localedir', get_option('prefix') / get_option('localedir'))
conf.set('pkgdatadir', pkgdatadir)

configure_file(
  input: 'photo-transfer-wizard.in',
  output: 'photo-transfer-wizard',
  configuration: conf,
  install: true,
  install_dir: get_option('bindir'),
  install_mode: 'r-xr-xr-x'
)

photo_transfer_wizard_sources = [
  '__init__.py',
  'main.py',
  'window.py',
]

install_data(photo_transfer_wizard_sources, install_dir: moduledir)
