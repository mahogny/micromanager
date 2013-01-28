find_path(LIBAGILENTLC_INCLUDE_DIR LaserCombinerSDK.h
           HINTS /usr/local/include/ )

find_library(LIBAGILENTLC_LIBRARY NAMES andorXYYZ  #I have no idea!
          HINTS /usr/local/lib/ )


if(EXISTS "${LIBAGILENTLC_INCLUDE_DIR}")



  set( mmgr_dal_AgilentLaserCombiner_SOURCES 
    AgilentLaserCombiner.cpp
    AgilentLaserCombiner.h
    )

  add_library(mmgr_dal_AgilentLaserCombiner SHARED ${mmgr_dal_AgilentLaserCombiner_SOURCES} )
  target_link_libraries( mmgr_dal_AgilentLaserCombiner MMCore dl z ${Boost_LIBRARIES} ${LIBAGILENTLC})

else()

  message(STATUS "Not adding Agilent laser combiner")

endif()















