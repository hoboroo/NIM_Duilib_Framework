aux_source_directory(${CMAKE_CURRENT_LIST_DIR} DIR_LIB_SRC)
aux_source_directory(${CMAKE_CURRENT_LIST_DIR}/Animation ANIMATION_SRC)
aux_source_directory(${CMAKE_CURRENT_LIST_DIR}/Automation AUTOMATION_SRC)
aux_source_directory(${CMAKE_CURRENT_LIST_DIR}/Box BOX_SRC)
aux_source_directory(${CMAKE_CURRENT_LIST_DIR}/Control CONTROL_SRC)
aux_source_directory(${CMAKE_CURRENT_LIST_DIR}/Core CORE_SRC)
aux_source_directory(${CMAKE_CURRENT_LIST_DIR}/Render RENDER_SRC)
aux_source_directory(${CMAKE_CURRENT_LIST_DIR}/Utils UTILS_SRC)

add_library(duilib
  ${DIR_LIB_SRC}
  ${ANIMATION_SRC}
  ${AUTOMATION_SRC}
  ${BOX_SRC}
  ${CONTROL_SRC}
  ${CORE_SRC}
  ${RENDER_SRC}
  ${UTILS_SRC}
)

target_link_libraries(duilib PUBLIC
  base
  comctl32
  gdiplus
  shlwapi
  imm32
  Msimg32
  winmm
)

target_compile_options(duilib PRIVATE /std:c++14)
target_compile_definitions(duilib PRIVATE UNICODE _UNICODE)
target_include_directories(duilib PUBLIC ${CMAKE_CURRENT_LIST_DIR})
