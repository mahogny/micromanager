
set( mmgr_dal_SerialManager_SOURCES 
  AsioClient.h
  SerialManager.cpp
  SerialManager.h
  )

add_library(mmgr_dal_SerialManager SHARED ${mmgr_dal_SerialManager_SOURCES} )
target_link_libraries( mmgr_dal_SerialManager MMCore dl z ${Boost_LIBRARIES} )
