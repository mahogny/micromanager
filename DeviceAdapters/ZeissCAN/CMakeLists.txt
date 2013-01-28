#project(MMCORE)

set( mmgr_dal_ZeissCAN_SOURCES 
  ZeissCAN.cpp 
  mcu28.cpp 
  ZStage.cpp 
  ZeissCAN.h
  )

add_library(mmgr_dal_ZeissCAN SHARED ${mmgr_dal_ZeissCAN_SOURCES} )
target_link_libraries( mmgr_dal_ZeissCAN MMCore dl z ${Boost_LIBRARIES} )


# This is mainly built to bundle with the JNI and Python bindings
#add_library(MMCore_static STATIC ${MMCore_SOURCES} )
#set_target_properties( MMCore_static PROPERTIES POSITION_INDEPENDENT_CODE TRUE )
