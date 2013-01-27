
find_package( Java REQUIRED )
include( UseJava )


find_jar(JAR_ABSOLUTELAYOUT AbsoluteLayout      PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_BSH            bsh-2.0b4           PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_CLOJURE        clojure             PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_CLOOJ          clooj               PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_COMMONS_MATH   commons-math-2.0    PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_CORE_CACHE     core.cache          PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_CORE_MEMOIZE   core.memoize        PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_DATA_JSON      data.json           PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_GPROTO         gproto              PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_IJ             ij                  PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_JCOMMON        jcommon-1.0.16      PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_JFREECHART     jfreechart-1.0.13   PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_LOCI_COMMON    loci-common         PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_LWM            lwm                 PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_OME_XML        ome-xml             PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_SCIFIO         scifio              PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_SLF4J_API      slf4j-api-1.7.1     PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_SUBSTANCE      substance           PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_SWING_LAYOUT   swing-layout-1.0.4  PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_SWINGX         swingx-0.9.5        PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_TRIDENT        trident             PATHS ../../../3rdpartypublic/classext/)
find_jar(JAR_TSFPROTO       TSFProto            PATHS ../../../3rdpartypublic/classext/)


find_jar(JAR_LOCI_TOOLS     loci_tools          PATHS ../../../3rdpartypublic/loci/)                  
set(JAR_MMCORE ${CMAKE_BINARY_DIR}/MMCoreJ_wrap/MMCoreJ.jar)

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

