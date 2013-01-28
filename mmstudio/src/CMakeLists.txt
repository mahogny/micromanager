include ( ../../cmake-java-common.txt )


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
  org/micromanager/api/MMWindow.java   ## why do I need to name it specifically? scary!!!
  org/micromanager/acquisition/*
  org/micromanager/conf2/*
  org/micromanager/graph/*
  org/micromanager/icons/*
  org/micromanager/navigation/*
  org/micromanager/script/*
  org/micromanager/utils/*
)



#note: json already included in mmcorej!

