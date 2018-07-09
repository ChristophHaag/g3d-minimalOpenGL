cmake_minimum_required(VERSION 2.6)
project(minimalOpenGL)

file(COPY ${CMAKE_SOURCE_DIR}/min.vrt DESTINATION .)
file(COPY ${CMAKE_SOURCE_DIR}/min.pix DESTINATION .)
file(COPY ${CMAKE_SOURCE_DIR}/color.bmp DESTINATION .)


find_package(GLEW)
find_package(glfw3)
find_package(OpenGL)

include_directories(${CMAKE_SOURCE_DIR})
link_directories(${CMAKE_SOURCE_DIR}/openvr/bin/linux64)


add_executable(minimalOpenGL main.cpp)

target_link_libraries(minimalOpenGL glfw ${GLEW_LIBRARIES} ${OPENGL_LIBRARIES} openvr_api)

install(TARGETS minimalOpenGL RUNTIME DESTINATION bin)

