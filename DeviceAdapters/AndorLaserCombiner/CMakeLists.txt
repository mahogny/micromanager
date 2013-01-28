find_path(LIBANDORLC_INCLUDE_DIR /usr/local/include/ALC_REV.h
           HINTS /usr/local/include/ )

find_library(LIBANDORLC_LIBRARY NAMES andor  #I have no idea!
          HINTS /usr/local/lib/ )


if(EXISTS "${LIBANDORLC_INCLUDE_DIR}")

  set( mmgr_dal_AndorLaserCombiner_SOURCES 
    AndorLaserCombiner.cpp
    AndorLaserCombiner.h
    )

  add_library(mmgr_dal_AndorLaserCombiner SHARED ${mmgr_dal_AndorLaserCombiner_SOURCES} )
  target_link_libraries( mmgr_dal_AndorLaserCombiner MMCore dl z ${Boost_LIBRARIES} ${LIBANDORLC_LIBRARY} )

else()
  message(STATUS "Not adding Andor laser combiner")
endif()
