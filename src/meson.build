
libdfu = shared_library('dfu',
  'dfu_load.c',
  'dfu_util.c',
  'dfuse.c',
  'dfuse_mem.c',
  'dfu.c',
  'dfu_file.c',
  'quirks.c',
  'variables.c',
  include_directories: rootInclude,
  dependencies: [
    libusb,
  ],
  install: true,
)

executable('dfu-util',
  'main.c',
  include_directories: rootInclude,
  link_with: libdfu,
  dependencies: [
    libusb,
  ],
  install: true,
)

executable('dfu-prefix',
  'prefix.c',
  include_directories: rootInclude,
  link_with: libdfu,
  dependencies: [
    libusb,
  ],
  install: true,
)

executable('dfu-suffix',
  'suffix.c',
  include_directories: rootInclude,
  link_with: libdfu,
  dependencies: [
    libusb,
  ],
  install: true,
)
