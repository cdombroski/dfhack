PROJECT (rendermax)

# A list of source files
SET(PROJECT_SRCS
    rendermax.cpp
	renderer_light.cpp
)
# A list of headers
SET(PROJECT_HDRS
    renderer_opengl.hpp
	renderer_light.hpp
)
SET_SOURCE_FILES_PROPERTIES( ${PROJECT_HDRS} PROPERTIES HEADER_FILE_ONLY TRUE)

# mash them together (headers are marked as headers and nothing will try to compile them)
LIST(APPEND PROJECT_SRCS ${PROJECT_HDRS})

# this makes sure all the stuff is put in proper places and linked to dfhack
DFHACK_PLUGIN(rendermax ${PROJECT_SRCS} LINK_LIBRARIES lua dfhack-tinythread)
install(FILES rendermax.lua
        DESTINATION ${DFHACK_DATA_DESTINATION}/raw)
