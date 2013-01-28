find_path(LIBANDOR_INCLUDE_DIR atmcdLXd.h 
           HINTS /usr/local/include/ )

find_library(LIBANDOR_LIBRARY NAMES andor  #I have no idea!
          HINTS /usr/local/lib/ )


if(EXISTS "${LIBANDOR_INCLUDE_DIR}")


  set( mmgr_dal_Andor_SOURCES 
    Andor.cpp
    Andor.h
    )

  add_library(mmgr_dal_Andor SHARED ${mmgr_dal_Andor_SOURCES} )
  target_link_libraries( mmgr_dal_Andor MMCore dl z ${Boost_LIBRARIES} ${LIBANDOR_LIBRARY} )

else()

  message(STATUS "Not adding Andor cameras")

endif()
