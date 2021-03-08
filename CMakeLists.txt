cmake_minimum_required(VERSION 3.17)
project(ImCalcInputTesting)
add_executable(ImCalcInputTesting)

set(CMAKE_CXX_STANDARD 17)

# OpenGL
set(OpenGL_GL_PREFERENCE GLVND)
find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIRS})
target_link_libraries(ImCalcInputTesting ${OPENGL_LIBRARIES})
if (UNIX)
    if (APPLE)
        target_link_libraries(ImCalcInputTesting "-framework Cocoa")
        target_link_libraries(ImCalcInputTesting "-framework IOKit")
        target_link_libraries(ImCalcInputTesting "-framework CoreVideo")
    endif ()
endif ()

# GLFW
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
add_subdirectory(lib/glfw lib/glfw/bin)
include_directories(${GLFW_INCLUDE_DIRS})
target_link_libraries(ImCalcInputTesting glfw)
target_link_libraries(ImCalcInputTesting ${GLFW_LIBRARIES})
if (UNIX)# todo check if this is necessary
    if (NOT APPLE)
        find_package(X11 REQUIRED)
        target_link_libraries(ImCalcInputTesting ${X11_LIBRARIES})
    endif ()
endif ()

# GLUT
find_package(GLUT REQUIRED)
include_directories(${GLUT_INCLUDE_DIRS})
target_link_libraries(ImCalcInputTesting ${GLUT_LIBRARY})

add_subdirectory(src)
add_subdirectory(lib)

if (WIN32)
    target_link_libraries(ImCalcInputTesting -lssp) # stack smashing protection
elseif (UNIX AND NOT APPLE)
    target_link_libraries(ImCalcInputTesting -ltbb)
endif ()

target_link_libraries(ImCalcInputTesting ${CMAKE_DL_LIBS})

#set(CMAKE_VERBOSE_MAKEFILE ON) # useful for fixing build errors