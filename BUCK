load('//:utils.bzl', 'extract', 'extractFolder')

version = '3.14.12'

http_archive(
  name = 'realm-sync-cocoa-archive',
  out = 'out',
  urls = [
    'https://static.realm.io/downloads/sync/realm-sync-cocoa-' + version + '.tar.xz',
  ],
  sha256 = '7dd66ea5f02e28b7b1bc64cbbcedd2a1ab29ab5e689c272cb73392616acdd978',
)

prebuilt_cxx_library(
  name = 'realm', 
  header_dirs = [
    extractFolder(':realm-sync-cocoa-archive', 'core/include'),
  ],
  preferred_linkage = 'static', 
  platform_static_lib = [
    ('macos.*', extract(':realm-sync-cocoa-archive', 'core/librealm-macosx.a')),
    ('iphone.*', extract(':realm-sync-cocoa-archive', 'core/librealm-ios.a')),
  ], 
  visibility = [
    'PUBLIC',
  ],
)

prebuilt_cxx_library(
  name = 'realm-parser', 
  preferred_linkage = 'static', 
  platform_static_lib = [
    ('macos.*', extract(':realm-sync-cocoa-archive', 'core/librealm-parser-macosx.a')),
    ('iphone.*', extract(':realm-sync-cocoa-archive', 'core/librealm-parser-ios.a')),
  ], 
  deps = [
    ':realm',
  ],
  visibility = [
    'PUBLIC',
  ],
)
