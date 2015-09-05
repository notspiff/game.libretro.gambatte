project(game.libretro.gambatte)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(kodi REQUIRED)
find_package(libretro-gambatte REQUIRED)

set(DEPLIBS gambatte)
set(GAMBATTE_CUSTOM_BINARY ${GAMBATTE_LIB}
                           game.libretro.gambatte${CMAKE_SHARED_LIBRARY_SUFFIX} gambatte)

build_addon(game.libretro.gambatte GAMBATTE DEPLIBS)
