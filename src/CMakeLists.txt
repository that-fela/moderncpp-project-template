# Set the executable output directory
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# GLOB all cpp files
file(GLOB_RECURSE SRC_FILES ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)

# Source files
add_executable(${BIN_NAME} ${SRC_FILES})
target_link_libraries(${BIN_NAME} ${LIBRARIES})
