
set( mmgr_dal_Aladdin_SOURCES 
  Aladdin.cpp
  Aladdin.h
  )

add_library(mmgr_dal_Aladdin SHARED ${mmgr_dal_Aladdin_SOURCES} )
target_link_libraries( mmgr_dal_Aladdin MMCore dl z ${Boost_LIBRARIES} )
