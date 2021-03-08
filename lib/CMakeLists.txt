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

set(im_calc_input_sources
        ImCalcInput/im_calc_input.cpp
        ImCalcInput/im_calc_input.h
        )

set(other_libs
        glad.c
        IconFontCppHeaders/IconsFontAwesome5.h
        fa_solid_900.cpp
        fa_solid_900.h
        roboto_regular.cpp
        roboto_regular.h
        )

target_sources(ImCalcInputTesting PUBLIC
        ${imgui_sources}
        ${im_calc_input_sources}
        ${other_libs}
        )

target_include_directories(ImCalcInputTesting PUBLIC imgui)
target_include_directories(ImCalcInputTesting PUBLIC IconFontCppHeaders)

target_compile_definitions(ImCalcInputTesting PUBLIC IMGUI_DISABLE_OBSOLETE_FUNCTIONS)
target_compile_definitions(ImCalcInputTesting PUBLIC IMGUI_DISABLE_WIN32_FUNCTIONS)