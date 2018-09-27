
project('dfu-util',
  'c',
  version: '0.9',
  meson_version: '>=0.47.0',
)
project_url = 'https://sourceforge.net/p/dfu-util'

config = configuration_data()
cc = meson.get_compiler('c')

config.set_quoted('PACKAGE',          meson.project_name())
config.set_quoted('PACKAGE_VERSION',  meson.project_version())
config.set_quoted('PACKAGE_STRING',   meson.project_name() + ' ' + meson.project_version())
config.set_quoted('PACKAGE_BUGREPORT',project_url)

###############################################################################
# Dependencies

# On FreeBSD the libusb-1.0 is called libusb and resides in system location
libusb = dependency('libusb-1.0', version: '>=1.0.0')

# Checks for header files.
check_headers = [
  'sysexits.h',
  'unistd.h',
  'windows.h',
]
foreach header : check_headers
  header_macro = 'HAVE_' + header.underscorify().to_upper()
  config.set(header_macro, cc.has_header(header))
endforeach

# Check for functions
check_functions = [
  'getpagesize',
  'nanosleep',
  'err',
]
foreach function : check_functions
  function_macro = 'HAVE_' + function.underscorify().to_upper()
  config.set(function_macro, cc.has_function(function))
endforeach


configure_file(
  output: 'config.h',
  configuration: config,
)
rootInclude = include_directories('.')
add_project_arguments('-DHAVE_CONFIG_H', language: 'c')


subdir('src')
