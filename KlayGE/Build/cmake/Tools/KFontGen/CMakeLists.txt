SET(SOURCE_FILES
	${KLAYGE_PROJECT_DIR}/Tools/src/KFontGen/KFontGen.cpp
)

SET(EXTRA_INCLUDE_DIRS
	${KLAYGE_PROJECT_DIR}/../External/freetype/include
	${KLAYGE_PROJECT_DIR}/../kfont/include
)

SET(EXTRA_LINKED_DIRS
	${KLAYGE_PROJECT_DIR}/../External/freetype/objs/${KLAYGE_PLATFORM_NAME}
	${KLAYGE_PROJECT_DIR}/../kfont/lib/${KLAYGE_PLATFORM_NAME}
)

IF(NOT KLAYGE_COMPILER_MSVC)
	SET(EXTRA_LINKED_LIBRARIES ${EXTRA_LINKED_LIBRARIES}
		debug kfont${KLAYGE_OUTPUT_SUFFIX}${CMAKE_DEBUG_POSTFIX} optimized kfont${KLAYGE_OUTPUT_SUFFIX}
		${Boost_PROGRAM_OPTIONS_LIBRARY})
ENDIF()

SET(EXTRA_LINKED_LIBRARIES ${EXTRA_LINKED_LIBRARIES}
	debug freetype261${KLAYGE_OUTPUT_SUFFIX}${CMAKE_DEBUG_POSTFIX} optimized freetype261${KLAYGE_OUTPUT_SUFFIX})

SETUP_TOOL(KFontGen)
