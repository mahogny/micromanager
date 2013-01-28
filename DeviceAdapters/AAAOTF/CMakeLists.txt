#project(MMCORE)

set( mmgr_dal_AAAOTF_SOURCES 
  AAAOTF.cpp
  AAAOTF.h
  )

add_library(mmgr_dal_AAAOTF SHARED ${mmgr_dal_AAAOTF_SOURCES} )
target_link_libraries( mmgr_dal_AAAOTF MMCore dl z ${Boost_LIBRARIES} )
