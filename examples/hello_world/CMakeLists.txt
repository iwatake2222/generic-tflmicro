cmake_minimum_required(VERSION 3.0)

set(BinName "hello_world")
add_executable(${BinName} "")

target_link_libraries(
  ${BinName}
  "generic-tflmicro"
)

target_include_directories(${BinName}
  PUBLIC
  ${DIR_TFLMICRO}/
  ${DIR_TFLMICRO}/third_party/gemmlowp
  ${DIR_TFLMICRO}/third_party/flatbuffers/include
  ${DIR_TFLMICRO}/third_party/ruy
  ${DIR_TFLMICRO}/third_party/kissfft
)

file(GLOB_RECURSE SRC ${CMAKE_CURRENT_LIST_DIR}/*.c ${CMAKE_CURRENT_LIST_DIR}/*.cpp ${CMAKE_CURRENT_LIST_DIR}/*.cc ${CMAKE_CURRENT_LIST_DIR}/*.cxx ${CMAKE_CURRENT_LIST_DIR}/*.h ${CMAKE_CURRENT_LIST_DIR}/*.hpp)

target_sources(${BinName}
  PRIVATE
  ${SRC}
)
