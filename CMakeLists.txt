cmake_minimum_required(VERSION 2.6)
project(minimalOpenGL)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${gl_SOURCE_DIR}/cmake/sdl2")

INCLUDE(FindPkgConfig)

PKG_SEARCH_MODULE(SDL2 REQUIRED sdl2)
PKG_SEARCH_MODULE(SDL2IMAGE REQUIRED SDL2_image>=2.0.0)

find_package(GLEW)
find_package(glfw3)

find_package(OpenGL REQUIRED)
add_definitions("-no-pie") # fucking netbeans only recognizes binaries like that https://www.linuxquestions.org/questions/arch-29/netbeans-will-not-recognize-build-as-executable-4175620457/

include_directories(${SDL2_INCLUDE_DIR} ${SDL2_IMAGE_INCLUDE_DIR} ${SDL2_TTF_INCLUDE_DIR}
	${OPENGL_INCLUDE_DIR})


add_executable(minimalOpenGL main.cpp)

MESSAGE("Link SDL libraries: ${SDL2_LIBRARY} ${SDL2_IMAGE_LIBRARIES} ${SDL2_TTF_LIBRARIES}, include: ${SDL2_INCLUDE_DIR} ${SDL2_IMAGE_INCLUDE_DIR} ${SDL2_TTF_INCLUDE_DIR}")

target_link_libraries(minimalOpenGL ${SDL2_LIBRARIES} ${SDL2_IMAGE_LIBRARIES} ${SDL2_TTF_LIBRARIES} ${OPENGL_LIBRARIES} m)

install(TARGETS minimalOpenGL RUNTIME DESTINATION bin)

