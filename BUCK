load('//:subdir_glob.bzl', 'subdir_glob')
load('//:buckaroo_macros.bzl', 'buckaroo_deps_from_package')

macos_headers = {
  'config.h': 'src/config.h.macosx',
}

linux_headers = {
  'config.h': 'src/config.h.linux',
}

prebuilt_cxx_library(
  name = 'config',
  header_namespace = '',
  header_only = True,
  exported_platform_headers = [
    ('macos.*', macos_headers),
    ('linux.*', linux_headers),
  ],
  visibility = [
    'PUBLIC',
  ],
)

cxx_library(
  name = 'r3',
  header_namespace = '',
  exported_headers = subdir_glob([
    ('include', '**/*.h'),
    ('include', '**/*.hpp'),
  ], prefix = 'r3'),
  headers = subdir_glob([
    ('include', '**/*.h'),
    ('include', '**/*.hpp'),
    ('src', '**/*.h'),
  ]),
  srcs = glob([
    'src/**/*.c',
  ], exclude = [
    'src/gvc.c',
    'src/json.c',
  ]),
  deps = [
    ':config',
  ] + buckaroo_deps_from_package('github.com/buckaroo-pm/pcre'),
  visibility = [
    'PUBLIC',
  ],
)

