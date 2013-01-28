#project(MMCORE)

set( mmgr_dal_DemoCamera_SOURCES 
  DemoCamera.cpp
  DemoCamera.h
  WriteCompactTiffRGB.h
  )

add_library(mmgr_dal_DemoCamera SHARED ${mmgr_dal_DemoCamera_SOURCES} )
target_link_libraries( mmgr_dal_DemoCamera MMCore dl z ${Boost_LIBRARIES} )
