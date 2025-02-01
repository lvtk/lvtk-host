project ('lvtk', ['cpp', 'c'], 
    version : '3.0.0',
    meson_version : '>= 1.0.0',
    license : 'ISC',
    default_options: [
        'b_ndebug=if-release',
        'buildtype=release',
        'c_std=c99',
        'cpp_std=c++17',
    ])

lilv_dep = dependency('lilv-0', required: false)
suil_dep = dependency('suil-0', required: false)
lvtk_dep = dependency('lvtk-3', required: false)

lvtk_host_dep = declare_dependency (
    include_directories: include_directories('include'),
    dependencies: [ lvtk_dep, lilv_dep, suil_dep ]
)

lvtk_abi_version = 3

pkg = import ('pkgconfig')
pkg.generate (
    name        : 'LVTK Host',
    description : 'LV2 Plugin C++ Library',
    subdirs     : 'lvtk-@0@'.format (lvtk_abi_version),
    filebase    : 'lvtk-host-@0@'.format (lvtk_abi_version),
    version     : meson.project_version(),
    install_dir : get_option ('libdir') / 'pkgconfig',
    requires    : [ ])
