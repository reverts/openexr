# yue.nicholas@gmail.com

ADD_LIBRARY ( Iex
  IexBaseExc.cpp
  IexThrowErrnoExc.cpp
  )

ADD_DEFINITIONS ( -DIEX_EXPORTS )

INSTALL ( TARGETS
  Iex
  DESTINATION
  lib
)

INSTALL ( FILES 
  IexBaseExc.h
  IexMathExc.h
  IexThrowErrnoExc.h
  IexErrnoExc.h
  IexMacros.h
  Iex.h
  IexNamespace.h
  IexExport.h
  IexForward.h
  DESTINATION
  include/OpenEXR
)
