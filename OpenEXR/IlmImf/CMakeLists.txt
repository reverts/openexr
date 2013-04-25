# yue.nicholas@gmail.com

# OpenEXRConfig.h generation
IF (WIN32)
  FILE ( WRITE ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_HAVE_COMPLETE_IOMANIP 1\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_NAMESPACE Imf\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_NAMESPACE_ENTER namespace Imf\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_NAMESPACE_EXIT\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_INTERNAL_NAMESPACE Imf\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_INTERNAL_NAMESPACE_ENTER namespace Imf\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_INTERNAL_NAMESPACE_EXIT\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_VERSION_STRING \"2.0.0\"\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_PACKAGE_STRING \"OpenEXR 2.0.0\"\n" )
ELSEIF (APPLE)
  FILE ( WRITE ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_HAVE_DARWIN 1\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_HAVE_COMPLETE_IOMANIP 1\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_NAMESPACE Imf\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_NAMESPACE_ENTER namespace Imf\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_NAMESPACE_EXIT\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_INTERNAL_NAMESPACE Imf\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_INTERNAL_NAMESPACE_ENTER namespace Imf\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_INTERNAL_NAMESPACE_EXIT\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_VERSION_STRING \"2.0.0\"\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_PACKAGE_STRING \"OpenEXR 2.0.0\"\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#include <string.h>\n" )
ELSE ()
  # Linux
  FILE ( WRITE ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_HAVE_LINUX_PROCFS 1\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_HAVE_COMPLETE_IOMANIP 1\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_NAMESPACE Imf\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_NAMESPACE_ENTER namespace Imf\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_NAMESPACE_EXIT\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_INTERNAL_NAMESPACE Imf\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_INTERNAL_NAMESPACE_ENTER namespace Imf\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_IMF_INTERNAL_NAMESPACE_EXIT\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_VERSION_STRING \"2.0.0\"\n" )
  FILE ( APPEND ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h "#define OPENEXR_PACKAGE_STRING \"OpenEXR 2.0.0\"\n" )
ENDIF()

ADD_EXECUTABLE ( b44ExpLogTable
  b44ExpLogTable.cpp
  )
TARGET_LINK_LIBRARIES ( b44ExpLogTable
  Half
)
ADD_CUSTOM_COMMAND (
  TARGET b44ExpLogTable POST_BUILD
  COMMAND b44ExpLogTable > ${CMAKE_CURRENT_SOURCE_DIR}/b44ExpLogTable.h
  WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
)
SET_SOURCE_FILES_PROPERTIES(
  ${CMAKE_CURRENT_SOURCE_DIR}/b44ExpLogTable.h
  PROPERTIES HEADER_FILE_ONLY TRUE
  )
SET_SOURCE_FILES_PROPERTIES (
  ImfB44Compressor.cpp
  PROPERTIES
  OBJECT_DEPENDS
  ${CMAKE_CURRENT_SOURCE_DIR}/b44ExpLogTable.h
)

SET ( ILMIMF_SRCS
  ImfAttribute.cpp
  ImfBoxAttribute.cpp
  ImfCRgbaFile.cpp
  ImfChannelList.cpp
  ImfChannelListAttribute.cpp
  ImfFloatAttribute.cpp
  ImfFrameBuffer.cpp
  ImfHeader.cpp
  ImfIO.cpp
  ImfInputFile.cpp
  ImfIntAttribute.cpp
  ImfLineOrderAttribute.cpp
  ImfMatrixAttribute.cpp
  ImfOpaqueAttribute.cpp
  ImfOutputFile.cpp
  ImfRgbaFile.cpp
  ImfStringAttribute.cpp
  ImfVecAttribute.cpp
  ImfHuf.cpp
  ImfThreading.cpp
  ImfWav.cpp
  ImfLut.cpp
  ImfCompressor.cpp
  ImfRleCompressor.cpp
  ImfZipCompressor.cpp
  ImfPizCompressor.cpp
  ImfB44Compressor.cpp
  ImfMisc.cpp
  ImfCompressionAttribute.cpp
  ImfDoubleAttribute.cpp
  ImfConvert.cpp
  ImfPreviewImage.cpp
  ImfPreviewImageAttribute.cpp
  ImfVersion.cpp
  ImfChromaticities.cpp
  ImfChromaticitiesAttribute.cpp
  ImfKeyCode.cpp
  ImfKeyCodeAttribute.cpp
  ImfTimeCode.cpp
  ImfTimeCodeAttribute.cpp
  ImfRational.cpp
  ImfRationalAttribute.cpp
  ImfFramesPerSecond.cpp
  ImfStandardAttributes.cpp
  ImfStdIO.cpp
  ImfEnvmap.cpp
  ImfEnvmapAttribute.cpp
  ImfScanLineInputFile.cpp
  ImfTiledInputFile.cpp
  ImfTiledMisc.cpp
  ImfTiledOutputFile.cpp
  ImfTiledRgbaFile.cpp
  ImfTileDescriptionAttribute.cpp
  ImfTileOffsets.cpp
  ImfRgbaYca.cpp
  ImfPxr24Compressor.cpp
  ImfTestFile.cpp
  ImfStringVectorAttribute.cpp
  ImfMultiView.cpp
  ImfAcesFile.cpp
  ImfMultiPartOutputFile.cpp
  ImfGenericOutputFile.cpp
  ImfOutputPartData.cpp
  ImfMultiPartInputFile.cpp
  ImfGenericInputFile.cpp
  ImfPartType.cpp
  ImfInputPartData.cpp
  ImfOutputPart.cpp
  ImfTiledOutputPart.cpp
  ImfInputPart.cpp
  ImfTiledInputPart.cpp
  ImfDeepScanLineInputPart.cpp
  ImfDeepScanLineOutputPart.cpp
  ImfDeepScanLineInputFile.cpp
  ImfDeepScanLineOutputFile.cpp
  ImfDeepTiledInputPart.cpp
  ImfDeepTiledOutputPart.cpp
  ImfDeepTiledInputFile.cpp
  ImfDeepTiledOutputFile.cpp
  ImfDeepFrameBuffer.cpp
  ImfDeepCompositing.cpp
  ImfCompositeDeepScanLine.cpp
)

ADD_LIBRARY ( IlmImf 
  ${ILMIMF_SRCS}
)

ADD_DEFINITIONS( -DILMIMF_EXPORTS )

SET ( ILMIMF_TARGET_LIBS Imath IlmThread Iex Half ${Z_LIB} )

IF (WIN32)
  SET (ILMIMF_TARGET_LIBS_DEBUG)
  SET (ILMIMF_TARGET_LIBS_OPT)
  FOREACH ( d ${ILMIMF_TARGET_LIBS} )
    LIST ( APPEND ILMIMF_TARGET_LIBS_DEBUG debug ${d}_d )
    LIST ( APPEND ILMIMF_TARGET_LIBS_OPT optimized ${d} )
  ENDFOREACH ()
  SET (ILMIMF_TARGET_LIBS ${ILMIMF_TARGET_LIBS_DEBUG} ${ILMIMF_TARGET_LIBS_OPT})
ENDIF ()

TARGET_LINK_LIBRARIES ( IlmImf ${ILMIMF_TARGET_LIBS} )

ADD_DEPENDENCIES ( IlmImf b44ExpLogTable )

# Libraries

INSTALL ( TARGETS
  IlmImf
  DESTINATION
  ${CMAKE_INSTALL_PREFIX}/lib
)

SET_TARGET_PROPERTIES ( IlmImf
  PROPERTIES
  VERSION 20.0.0
  SOVERSION 20
  DEBUG_POSTFIX _d
  )

# Headers
INSTALL ( FILES
  ${CMAKE_SOURCE_DIR}/config/OpenEXRConfig.h
  ImfAcesFile.h
  ImfArray.h
  ImfAttribute.h
  ImfB44Compressor.h
  ImfBoxAttribute.h
  ImfChannelListAttribute.h
  ImfChannelList.h
  ImfChromaticitiesAttribute.h
  ImfChromaticities.h
  ImfCompositeDeepScanLine.h
  ImfCompressionAttribute.h
  ImfCompression.h
  ImfConvert.h
  ImfCRgbaFile.h
  ImfDeepCompositing.h
  ImfDeepFrameBuffer.h
  ImfDeepScanLineInputFile.h
  ImfDeepScanLineInputPart.h
  ImfDeepScanLineOutputFile.h
  ImfDeepScanLineOutputPart.h
  ImfDeepTiledInputFile.h
  ImfDeepTiledInputPart.h
  ImfDeepTiledOutputFile.h
  ImfDeepTiledOutputPart.h
  ImfDoubleAttribute.h
  ImfEnvmapAttribute.h
  ImfEnvmap.h
  ImfExport.h
  ImfFloatAttribute.h
  ImfForward.h
  ImfFrameBuffer.h
  ImfFramesPerSecond.h
  ImfGenericInputFile.h
  ImfGenericOutputFile.h
  ImfHeader.h
  ImfHuf.h
  ImfInputFile.h
  ImfInputPart.h
  ImfInt64.h
  ImfIntAttribute.h
  ImfIO.h
  ImfKeyCodeAttribute.h
  ImfKeyCode.h
  ImfLineOrderAttribute.h
  ImfLineOrder.h
  ImfLut.h
  ImfMatrixAttribute.h
  ImfMultiPartInputFile.h
  ImfMultiPartOutputFile.h
  ImfMultiView.h
  ImfName.h
  ImfNamespace.h
  ImfOpaqueAttribute.h
  ImfOutputFile.h
  ImfOutputPart.h
  ImfPartHelper.h
  ImfPartType.h
  ImfPixelType.h
  ImfPreviewImageAttribute.h
  ImfPreviewImage.h
  ImfRationalAttribute.h
  ImfRational.h
  ImfRgbaFile.h
  ImfRgba.h
  ImfRgbaYca.h
  ImfStandardAttributes.h
  ImfStdIO.h
  ImfStringAttribute.h
  ImfStringVectorAttribute.h
  ImfTestFile.h
  ImfThreading.h
  ImfTileDescriptionAttribute.h
  ImfTileDescription.h
  ImfTiledInputFile.h
  ImfTiledInputPart.h
  ImfTiledOutputFile.h
  ImfTiledOutputPart.h
  ImfTiledRgbaFile.h
  ImfTimeCodeAttribute.h
  ImfTimeCode.h
  ImfVecAttribute.h
  ImfVersion.h
  ImfWav.h
  ImfXdr.h
  DESTINATION
  ${CMAKE_INSTALL_PREFIX}/include/OpenEXR
  )
