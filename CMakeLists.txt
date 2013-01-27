cmake_minimum_required(VERSION 2.6)
project(MMLIBS)

## Options
option(USE_SWIG_BINDINGS "Java and Python bindings" ON)
option(BUILD_MMSTUDIO "MM studio" ON)

## Main package
set(Boost_USE_STATIC_LIBS OFF)
set(Boost_USE_MULTITHREADED ON) 
set(Boost_USE_STATIC_RUNTIME OFF)
find_package(Boost REQUIRED COMPONENTS date_time exception system thread)

# Top-level include since Boost is also used by DeviceAdapters
include_directories(${Boost_INCLUDE_DIR})

# Top-level include since MMCore is used by bindings, DeviceAdapters,
# and example DeviceAdapters
include_directories("${PROJECT_SOURCE_DIR}/MMCore")
add_subdirectory(MMDevice)
add_subdirectory(MMCore)

# TODO Make SimpleAutoFocus DeviceAdapter include
# ${PROJECT_SOURCE_DIR}/Util
#add_subdirectory(DeviceAdapters)

## Bindings
if(USE_SWIG_BINDINGS)
  find_package(SWIG REQUIRED)
  add_subdirectory(MMCoreJ_wrap)
  add_subdirectory(MMCorePy_wrap)
endif()


## Macro
MACRO(HEADER_DIRECTORIES return_list)
    FILE(GLOB_RECURSE new_list "plugins/*")
    SET(dir_list "")
    FOREACH(file_path ${new_list})
        SET(dir_list ${file_path} )
    ENDFOREACH()
    LIST(REMOVE_DUPLICATES dir_list)
    SET(${return_list} ${dir_list})
ENDMACRO()

## MM studio
if(BUILD_MMSTUDIO)
  add_subdirectory(mmstudio/src)
#  HEADER_DIRECTORIES(retlist)
  file (GLOB retlist "plugins/*/src")
  foreach(PLUGIN ${retlist})
    message(STATUS ${PLUGIN})
    add_subdirectory(${PLUGIN})
  endforeach()
#  include_directories(plugins/*/src)
#  add_subdirectory(plugins/BFCorrector/src)
endif()

## Documentation
#add_subdirectory(DeviceKit)
#add_subdirectory(Tutorial)
#add_subdirectory(doc)
