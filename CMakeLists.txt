cmake_minimum_required(VERSION 3.18)

project(bannertool)

# add definition for alloca
# otherwise stb_vorbis fails
if(MSVC)
    add_compile_definitions(alloca=_alloca)
endif()

# define version
set(VERSION_MAJOR "1")
set(VERSION_MINOR "2")
set(VERSION_MICRO "0")

# Add executable
add_executable(bannertool
source/cmd.cpp
source/main.cpp
source/pc/stb_image.c
source/pc/stb_vorbis.c
source/pc/wav.cpp
source/3ds/cbmd.cpp
source/3ds/cwav.cpp
source/3ds/lz11.cpp)
# set include dirs
target_include_directories(bannertool PUBLIC
source
source/3ds
source/pc)
# define VERSION
target_compile_definitions(bannertool PUBLIC
-DVERSION_MAJOR=${VERSION_MAJOR}
-DVERSION_MINOR=${VERSION_MINOR}
-DVERSION_MICRO=${VERSION_MICRO})

install(TARGETS bannertool DESTINATION bin)