set(imgui_sources
        imgui/backends/imgui_impl_glfw.cpp
        imgui/backends/imgui_impl_glfw.h
        imgui/backends/imgui_impl_opengl3.cpp
        imgui/backends/imgui_impl_opengl3.h
        imgui/imconfig.h
        imgui/imgui.cpp
        imgui/imgui.h
        imgui/imgui_demo.cpp
        imgui/imgui_draw.cpp
        imgui/imgui_internal.h
        imgui/imgui_tables.cpp
        imgui/imgui_widgets.cpp
        imgui/imstb_rectpack.h
        imgui/imstb_textedit.h
        imgui/imstb_truetype.h
        )

set(other_libs
        glad.c
        IconFontCppHeaders/IconsFontAwesome5.h
        )

target_sources(ImCalcInputTesting PUBLIC
        ${imgui_sources}
        ${other_libs}
        )

target_include_directories(ImCalcInputTesting PUBLIC imgui)

target_compile_definitions(ImCalcInputTesting PUBLIC IMGUI_DISABLE_OBSOLETE_FUNCTIONS)
target_compile_definitions(ImCalcInputTesting PUBLIC IMGUI_DISABLE_WIN32_FUNCTIONS)