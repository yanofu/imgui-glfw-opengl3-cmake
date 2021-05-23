cmake_minimum_required(VERSION 3.0.0)
project(sample VERSION 0.0.0)

find_package(OpenGL)

set(IMGUI_SOURCE_DIR ${CMAKE_SOURCE_DIR}/imgui)
set(IMGUI_BACKENDS_DIR ${IMGUI_SOURCE_DIR}/backends)
set(IMGUI_LIBS_DIR ${IMGUI_SOURCE_DIR}/examples/libs)
set(GL3W_SOURCE_DIR ${IMGUI_LIBS_DIR}/gl3w)
set(GLFW_INCLUDE_DIR ${IMGUI_LIBS_DIR}/glfw/include)
set(GLFW_LIB ${IMGUI_LIBS_DIR}/glfw/lib-vc2010-64/glfw3.lib)

set(SOURCE_FILES
    ${IMGUI_SOURCE_DIR}/examples/example_glfw_opengl3/main.cpp
    ${IMGUI_SOURCE_DIR}/imgui_demo.cpp
    ${IMGUI_SOURCE_DIR}/imgui_draw.cpp
    ${IMGUI_SOURCE_DIR}/imgui_tables.cpp
    ${IMGUI_SOURCE_DIR}/imgui.cpp
    ${IMGUI_SOURCE_DIR}/imgui_widgets.cpp
    ${IMGUI_BACKENDS_DIR}/imgui_impl_opengl3.cpp
    ${IMGUI_BACKENDS_DIR}/imgui_impl_glfw.cpp
    ${GL3W_SOURCE_DIR}/GL/gl3w.c
)

add_executable(sample ${SOURCE_FILES})

target_include_directories(sample PRIVATE
    ${IMGUI_SOURCE_DIR}
    ${IMGUI_BACKENDS_DIR}
    ${GLFW_INCLUDE_DIR}
    ${GL3W_SOURCE_DIR}
)

target_link_libraries(sample
    OpenGL::GL
    ${GLFW_LIB}
)