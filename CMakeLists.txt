project(gameclient.gambatte)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(xbmc REQUIRED)

include(ExternalProject)

externalproject_add(gambatte
                    GIT_REPOSITORY https://github.com/libretro/gambatte-libretro
                    GIT_TAG ff69a30
                    PREFIX gambatte
                    CONFIGURE_COMMAND ""
                    INSTALL_COMMAND ""
                    BUILD_COMMAND make -C libgambatte/ -f Makefile.libretro
                    BUILD_IN_SOURCE 1)

set(GAMBATTE_CUSTOM_BINARY ${PROJECT_BINARY_DIR}/gambatte/src/gambatte/libgambatte/gambatte_libretro${CMAKE_SHARED_LIBRARY_SUFFIX}
                        gambatte_libretro${CMAKE_SHARED_LIBRARY_SUFFIX} gambatte)

build_addon(gameclient.gambatte GAMBATTE DEPLIBS)
add_dependencies(gameclient.gambatte gambatte)
