
find_package( Java REQUIRED )
include( UseJava )


#find_jar(JAR_BEANSHELL       bsh-2.0b4.jar          PATHS ../../../3rdpartypublic/classext/)
#find_jar(JAR_IJ              /home/mahogny/git/3rdpartypublic/classext/ij.jar)
#find_jar(JAR_ABSOLUTE_LAYOUT AbsoluteLayout.jar     PATHS ../../../3rdpartypublic/classext/)
#find_jar(JAR_CLOJURE         clojure.jar            PATHS ../../../3rdpartypublic/classext/)
#find_jar(JAR_CLOOJ           clooj.jar              PATHS ../../../3rdpartypublic/classext/)
#find_jar(JAR_C_MATH          commons-math-2.0.jar   PATHS ../../../3rdpartypublic/classext/)
#find_jar(JAR_DATAJSON        data.json.jar          PATHS ../../../3rdpartypublic/classext/)
#find_jar(JAR_JCOMMON         jcommon-1.0.16.jar     PATHS ../../../3rdpartypublic/classext/)
#find_jar(JAR_JFREECHART      jfreechart-1.0.13.jar  PATHS ../../../3rdpartypublic/classext/)
#find_jar(JAR_SWING_LAYOUT    swing-layout-1.0.4.jar PATHS ../../../3rdpartypublic/classext/)
#find_jar(JAR_SWINGX          swingx.jar             PATHS ../../../3rdpartypublic/classext/)
#find_jar(JAR_LOCI_TOOLS      loci_tools.jar         PATHS ../../../3rdpartypublic/loci/)


#problem with above. hack follows
set(JAR_ABSOLUTELAYOUT ../../../3rdpartypublic/classext/AbsoluteLayout.jar)
set(JAR_BSH            ../../../3rdpartypublic/classext/bsh-2.0b4.jar)
set(JAR_CLOJURE        ../../../3rdpartypublic/classext/clojure.jar)
set(JAR_CLOOJ          ../../../3rdpartypublic/classext/clooj.jar)
set(JAR_COMMONS_MATH   ../../../3rdpartypublic/classext/commons-math-2.0.jar)
set(JAR_CORE_CACHE     ../../../3rdpartypublic/classext/core.cache.jar)
set(JAR_CORE_MEMOIZE   ../../../3rdpartypublic/classext/core.memoize.jar)
set(JAR_DATA_JSON      ../../../3rdpartypublic/classext/data.json.jar)
set(JAR_GPROTO         ../../../3rdpartypublic/classext/gproto.jar)
set(JAR_IJ             ../../../3rdpartypublic/classext/ij.jar)
set(JAR_JCOMMON        ../../../3rdpartypublic/classext/jcommon-1.0.16.jar)
set(JAR_JFREECHART     ../../../3rdpartypublic/classext/jfreechart-1.0.13.jar)
set(JAR_LOCI_COMMON    ../../../3rdpartypublic/classext/loci-common.jar)
set(JAR_LWM            ../../../3rdpartypublic/classext/lwm.jar)
set(JAR_OME_XML        ../../../3rdpartypublic/classext/ome-xml.jar)
set(JAR_SCIFIO         ../../../3rdpartypublic/classext/scifio.jar)
set(JAR_SLF4J_API      ../../../3rdpartypublic/classext/slf4j-api-1.7.1.jar)
set(JAR_SUBSTANCE      ../../../3rdpartypublic/classext/substance.jar)
set(JAR_SWING_LAYOUT   ../../../3rdpartypublic/classext/swing-layout-1.0.4.jar)
set(JAR_SWINGX         ../../../3rdpartypublic/classext/swingx-0.9.5.jar)
set(JAR_TRIDENT        ../../../3rdpartypublic/classext/trident.jar)
set(JAR_TSFPROTO       ../../../3rdpartypublic/classext/TSFProto.jar)


set(JAR_LOCI_TOOLS     ../../../3rdpartypublic/loci/loci_tools.jar)                  
set(JAR_MMCORE         ../../build/MMCoreJ_wrap/MMCoreJ.jar)                   ###baaad!


set(CMAKE_JAVA_INCLUDE_PATH 
 ${JAR_ABSOLUTELAYOUT}
 ${JAR_BSH}
 ${JAR_CLOJURE}
 ${JAR_CLOOJ}
 ${JAR_COMMONS_MATH}
 ${JAR_CORE_CACHE}
 ${JAR_CORE_MEMOIZE}
 ${JAR_DATA_JSON}
 ${JAR_GPROTO}
 ${JAR_IJ}
 ${JAR_JCOMMON}
 ${JAR_JFREECHART}
 ${JAR_LOCI_COMMON}
 ${JAR_LWM}
 ${JAR_OME_XML}
 ${JAR_SCIFIO}
 ${JAR_SLF4J_API}
 ${JAR_SUBSTANCE}
 ${JAR_SWING_LAYOUT}
 ${JAR_SWINGX}
 ${JAR_TRIDENT}
 ${JAR_TSFPROTO}
 ${JAR_LOCI_TOOLS}
 ${JAR_MMCORE}
)


#these should go into the jar as well:
#  MANIFEST.MF
#  plugins_mmstudio.config
#  plugins_reader.config


add_jar(mmstudio 
  *.java
  com/quirkware/guid/*
  org/jeditsyntax/*
  org/json/*
  org/micromanager/*
  org/micromanager/api/*
  org/micromanager/acquisition/*
  org/micromanager/conf2/*
  org/micromanager/graph/*
  org/micromanager/icons/*
  org/micromanager/navigation/*
  org/micromanager/script/*
  org/micromanager/utils/*
)



#note: json already included in mmcorej!

