
set(exe_name "imgui-sdl-src")


##################################
#        Extra definitions       #
##################################

add_definitions(-std=c++11)

##################################
#       Gather Dependencies      #
##################################

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake_modules/")

set(LIBRARY
    DruidImgui-Dep
    DruidSDL-Dep
    DruidOpenGL-Dep
)


##################################
#          Build Binary          #
##################################

FILE(GLOB_RECURSE source_files RELATIVE ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/src/*.c*
)
FILE(GLOB_RECURSE header_files RELATIVE ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/src/*.h*
)

add_library(${exe_name}
    STATIC
    ${source_files}
    ${header_files}
)

# add_executable(${exe_name} ${source_files} ${header_files})
# add_test(${exe_name} ${exe_name})

target_link_libraries(${exe_name}
    ${LIBRARY}
)
target_include_directories(${exe_name}
    PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/src
    ${INCLUDE}
)

##################################
#       sort out resources       #
##################################
