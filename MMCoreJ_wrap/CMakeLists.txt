
find_package( SWIG REQUIRED )
include( ${SWIG_USE_FILE} )

find_package( Java REQUIRED )
include( UseJava )

# Discover JNI path
if( NOT JDK_PATH )
  get_filename_component( JAVAC_REALPATH ${Java_JAVAC_EXECUTABLE} REALPATH )
  get_filename_component( JDK_HINT ${JAVAC_REALPATH} PATH )
  get_filename_component( JDK_HINT ${JDK_HINT} PATH )

  set( JDK_PATH ${JDK_HINT} CACHE PATH "Location of the JDK" )
 endif()

# JNI headers
find_path( JDK_INCLUDE jni.h HINTS ${JDK_PATH}/include )
string( TOLOWER ${CMAKE_SYSTEM_NAME} JDK_PLATFORM_GUESS )
set( JDK_PLATFORM_TYPE ${JDK_PLATFORM_GUESS} CACHE STRING "Name of the platform-specific include directory for jni_md.h" )
find_path( JDK_PLATFORM_INCLUDE jni_md.h HINTS ${JDK_INCLUDE}/${JDK_PLATFORM_TYPE} ${JDK_INCLUDE} )

include_directories( ${JDK_INCLUDE} ${JDK_PLATFORM_INCLUDE} )

set(SWIGFLAGS -package mmcorej)

# Swig, convert to java
set_source_files_properties( MMCoreJ.i PROPERTIES CPLUSPLUS ON )
set_source_files_properties( MMCoreJ.i PROPERTIES SWIG_FLAGS "${SWIGFLAGS}" )
set( SWIG_MODULE_MMCoreJ_EXTRA_DEPS MMCore )
set( CMAKE_SWIG_OUTDIR mmcorej)
swig_add_module( MMCoreJ_wrap java MMCoreJ.i )
swig_link_libraries( MMCoreJ_wrap MMCore MMDevice )


# will not work

# Jar-file
#add_jar( MMCoreJ 
#  TaggedImage.java 
#  *.java
#  mmcorej/*.java    #doesn't get this far if included!
#  ../mmstudio/src/org/json/*.java     #TODO this is bad!
#)


#add_jar( MMCoreJ
#  TaggedImage.java
#  ${CMAKE_SWIG_OUTDIR}/*.java
#  ../mmstudio/src/org/json/*.java     #TODO this is bad!
#)


#http://www.cmake.org/pipermail/cmake/2010-April/036662.html

ADD_CUSTOM_COMMAND(TARGET MMCoreJ_wrap
                   POST_BUILD
  COMMAND cmake -E echo "Compiling Java files..."

  #this is BAD
  COMMAND mkdir -p mmstudio/src/org/json
  COMMAND cp ../../MMCoreJ_wrap/*.java mmcorej/
  COMMAND cp ../../mmstudio/src/org/json/*.java mmstudio/src/org/json   

  COMMAND javac mmcorej/*.java  mmstudio/src/org/json/*.java
  COMMAND cmake -E echo "Creating jar file..."
  COMMAND jar cvf MMCoreJ.jar mmcorej/*.class mmstudio/src/org/json/*.class
  COMMENT Assembling MMCoreJ.jar
)
