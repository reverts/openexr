# pstanczyk@ilm.com

ADD_LIBRARY ( IexMath
  IexMathFloatExc.cpp  
  IexMathFpu.cpp
  )

INSTALL ( TARGETS
  IexMath
  DESTINATION
  lib
)

ADD_DEFINITIONS ( -DIEXMATH_EXPORTS )

TARGET_LINK_LIBRARIES( IexMath
  Iex 
)

INSTALL ( FILES 
  IexMathFloatExc.h  
  IexMathFpu.h  
  IexMathIeeeExc.h
  IexMathExport.h
  DESTINATION
  include/OpenEXR
)
