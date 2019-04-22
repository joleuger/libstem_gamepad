project('libstem_gamepad',
  'c',
  version: '2019.05',
  license: 'zlib'
)

libstem_gamepad_build_include = include_directories('include','source')
libstem_gamepad_include = include_directories('include')

if target_machine.system() == 'linux'
  message('Build libstem_gamepad for linux.')

  thread_dep = dependency('threads')
  libstem_gamepad =  static_library('stem_gamepad',
    'source/gamepad/Gamepad_private.c',
    'source/gamepad/Gamepad_linux.c',
    dependencies: [thread_dep],
    include_directories : libstem_gamepad_build_include)

  libstem_gamepad_dep = declare_dependency(
    link_with: [libstem_gamepad],
    dependencies: [thread_dep],
    include_directories: [libstem_gamepad_include]
  )
elif target_machine.system() == 'darwin'
  message('Build libstem_gamepad for macOS.')
  CoreFoundation_dep = dependency('CoreFoundation')
  IOKit_dep = dependency('IOKit')

  thread_dep = dependency('threads')
  libstem_gamepad =  static_library('stem_gamepad',
    'source/gamepad/Gamepad_private.c',
    'source/gamepad/Gamepad_macosx.c',
    dependencies: [thread_dep],
    include_directories : libstem_gamepad_build_include)

  libstem_gamepad_dep = declare_dependency(
    link_with: [libstem_gamepad],
    dependencies: [thread_dep, CoreFoundation_dep, IOKit_dep],
    include_directories: [libstem_gamepad_include]
  )
elif target_machine.system() == 'windows'
  message('Target machine not supported by libstem_gamepad.')
  libstem_gamepad_dep = disabler()
else
  message('Target machine not supported by libstem_gamepad.')
  libstem_gamepad_dep = disabler()
endif
