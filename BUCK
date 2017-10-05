include_defs('//BUCKAROO_DEPS')

macos_headers = {
  'config.h': 'src/config.h.macosx',
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
    ('.*', macos_headers),
  ],
  srcs = glob([
    'src/**/*.c',
  ], excludes = [
    'src/gvc.c',
    'src/json.c',
  ]),
  deps = BUCKAROO_DEPS + [
    ':zmalloc',
  ],
  visibility = [
    'PUBLIC',
  ],
)

cxx_library(
  name = 'zmalloc',
  header_namespace = '',
  exported_headers = {
    'zmalloc.h': '3rdparty/zmalloc.h',
  },
  platform_headers = [
    ('^macos.*', macos_headers),
    ('.*', macos_headers),
  ],
  srcs = [
    '3rdparty/zmalloc.c',
  ],
)
