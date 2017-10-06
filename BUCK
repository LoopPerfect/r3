include_defs('//BUCKAROO_DEPS')

macos_headers = {
  'config.h': 'src/config.h.macosx',
}

linux_headers = {
  'config.h': 'src/config.h.linux',
}

cxx_library(
  name = 'r3',
  header_namespace = '',
  exported_headers = subdir_glob([
    ('include', '**/*.h'),
    ('include', '**/*.hpp'),
  ]),
  headers = subdir_glob([
    ('src', '**/*.h'),
  ]),
  platform_headers = [
    ('^macos.*', macos_headers),
    ('^linux.*', linux_headers),
    ('default', linux_headers),
  ],
  srcs = glob([
    'src/**/*.c',
  ], excludes = [
    'src/gvc.c',
    'src/json.c',
  ]),
  deps = BUCKAROO_DEPS,
  visibility = [
    'PUBLIC',
  ],
)

