cmake_minimum_required(VERSION 3.20)

file(GLOB_RECURSE MSDFGEN_CORE_HEADERS "${CMAKE_CURRENT_LIST_DIR}/msdfgen/core/*.h" "${CMAKE_CURRENT_LIST_DIR}/msdfgen/core/*.hpp")
file(GLOB_RECURSE MSDFGEN_CORE_SOURCES "${CMAKE_CURRENT_LIST_DIR}/msdfgen/core/*.cpp")
file(GLOB_RECURSE MSDFGEN_EXT_HEADERS  "${CMAKE_CURRENT_LIST_DIR}/msdfgen/ext/*.h" "${CMAKE_CURRENT_LIST_DIR}/msdfgen/ext/*.hpp")
file(GLOB_RECURSE MSDFGEN_EXT_SOURCES  "${CMAKE_CURRENT_LIST_DIR}/msdfgen/ext/*.cpp" "${CMAKE_CURRENT_LIST_DIR}/msdfgen/lib/*.cpp")

file(GLOB_RECURSE MSDF_ATLAS_GEN_HEADERS  "${CMAKE_CURRENT_LIST_DIR}/msdf-atlas-gen/*.h" "${CMAKE_CURRENT_LIST_DIR}/msdf-atlas-gen/*.hpp")
file(GLOB_RECURSE MSDF_ATLAS_GEN_SOURCES  "${CMAKE_CURRENT_LIST_DIR}/msdf-atlas-gen/*.cpp")

#message(Files ${MSDFGEN_CORE_HEADERS})


message("patate ${CMAKE_CURRENT_LIST_DIR}/../freetype/include ")

add_library(msdf-atlas-gen
        "${CMAKE_CURRENT_LIST_DIR}/msdfgen/msdfgen.h"
        ${MSDFGEN_CORE_HEADERS}
        ${MSDFGEN_CORE_SOURCES}
        ${MSDFGEN_EXT_HEADERS}
        ${MSDFGEN_EXT_SOURCES}
        ${MSDF_ATLAS_GEN_HEADERS}
        ${MSDF_ATLAS_GEN_SOURCES}
        )


target_include_directories(msdf-atlas-gen PUBLIC
        ${CMAKE_CURRENT_LIST_DIR}
        "${CMAKE_CURRENT_LIST_DIR}/msdfgen"
        "${CMAKE_CURRENT_LIST_DIR}/msdfgen/include"
        "${CMAKE_CURRENT_LIST_DIR}/msdfgen/core"
        "${CMAKE_CURRENT_LIST_DIR}/artery-font-format"
        "${CMAKE_CURRENT_LIST_DIR}/../freetype/include"
        )

#target_sources(${PROJECT_NAME} PUBLIC
#        "${CMAKE_CURRENT_LIST_DIR}/msdfgen/msdfgen.h"
#        ${MSDFGEN_CORE_HEADERS}
#        ${MSDFGEN_CORE_SOURCES}
#        ${MSDFGEN_EXT_HEADERS}
#        ${MSDFGEN_EXT_SOURCES}
#        ${MSDF_ATLAS_GEN_HEADERS}
#        ${MSDF_ATLAS_GEN_SOURCES}
#        )


