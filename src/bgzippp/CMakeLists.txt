
# executable

add_executable(bgzippp
    main.cpp
)


# dependencies

find_package(fmt CONFIG REQUIRED)
target_link_libraries(bgzippp PRIVATE fmt::fmt)


# build options

set_common_build_options(bgzippp)
