project(sb_imgui LANGUAGES CXX)

sbAddExecutable(sb_imgui
    src/main.cpp
    thirdparty/src/GL/gl3w.cpp
    thirdparty/src/imgui/imgui_demo.cpp
    thirdparty/src/imgui/imgui_draw.cpp
    thirdparty/src/imgui/imgui_widgets.cpp
    thirdparty/src/imgui/imgui.cpp
    thirdparty/src/imgui/imgui_impl_sdl.cpp
    thirdparty/src/imgui/imgui_impl_opengl3.cpp)

target_include_directories(sb_imgui
    PRIVATE
        ${CMAKE_CURRENT_LIST_DIR}/thirdparty/inc)

target_compile_options(sb_imgui
    PRIVATE 
        -Wno-reserved-id-macro
        -Wno-zero-as-null-pointer-constant
        -Wno-double-promotion
        -Wno-float-equal
        -Wno-sign-conversion
        -Wno-unused-macros
        -Wno-cast-qual)

# find_library(accelerate Accelerate)
# find_library(appKit AppKit)
# find_library(audioUnit AudioUnit)
# find_library(coreFoundation CoreFoundation)
# find_library(coreServices CoreServices)
# find_library(foundation Foundation)
# find_library(quartz Quartz)
# find_library(javascriptCore JavaScriptCore)
find_library(audioToolbox AudioToolbox)
find_library(carbon Carbon)
find_library(cocoa Cocoa)
find_library(coreAudio CoreAudio)
find_library(iokit IOKit)
find_library(quartzCore QuartzCore)
find_library(forceFeedback ForceFeedback)
find_library(iconv Iconv)

target_link_libraries(sb_imgui 
    PRIVATE
        sb::core
        ${CMAKE_CURRENT_LIST_DIR}/thirdparty/lib/macos_x86_64/libSDL2.a
        ${audioToolbox}
        ${carbon}
        ${cocoa}
        ${coreAudio}
        ${iokit}
        ${quartzCore}
        ${forceFeedback}
        ${iconv})
