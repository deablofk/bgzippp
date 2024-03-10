# cmake config

cmake_minimum_required(VERSION 3.20)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)


# project config

project(bgzippp VERSION 0.1.0 LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)


function(set_common_build_options executable)

    target_link_libraries(${executable} PRIVATE

        $<$<CONFIG:DEBUG>:-fsanitize=address>
        $<$<CONFIG:DEBUG>:-fsanitize=undefined>
    )

    target_compile_options(${executable} PRIVATE

        -std=c++20
        -pedantic -Wall -Wextra
        -Werror=switch
        -fdiagnostics-color=always

        $<$<CONFIG:DEBUG,RELWITHDEBINFO>:-g>
        $<$<CONFIG:RELEASE,RELWITHDEBINFO>:-O3>
    )

endfunction()


# targets

add_subdirectory(src/bgzippp bgzippp)
