cmake_minimum_required(VERSION 3.10)
project(wordpad CXX)

# Use MFC in a static library
set(CMAKE_MFC_FLAG 1)

# Set the output directory for the executable
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# Add the executable target with all the source files
add_executable(wordpad
    stdafx.cpp
    about.cpp
    bigicon.cpp
    buttondi.cpp
    chicdial.cpp
    cntritem.cpp
    colorlis.cpp
    datedial.cpp
    ddxm.cpp
    docopt.cpp
    doctype.cpp
    filenewd.cpp
    formatba.cpp
    formatpa.cpp
    formatta.cpp
    ipframe.cpp
    key.cpp
    listdlg.cpp
    mainfrm.cpp
    multconv.cpp
    options.cpp
    optionsh.cpp
    pageset.cpp
    ruler.cpp
    splash.cpp
    srvritem.cpp
    strings.cpp
    unitspag.cpp
    wordpad.cpp
    wordpdoc.cpp
    wordpvw.cpp
    wordpad.rc
)

# Set MSVC specific flags
if(MSVC)
    # Set the runtime library
    set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")

    # Add compile options
    target_compile_options(wordpad PRIVATE /W3 /EHsc)

    # Set the entry point
    set_target_properties(wordpad PROPERTIES LINK_FLAGS "/subsystem:windows /entry:wWinMainCRTStartup")
endif()

# Add precompiled header
target_precompile_headers(wordpad PRIVATE stdafx.h)

# Add compile definitions
target_compile_definitions(wordpad PRIVATE
    "WIN32"
    "_WINDOWS"
    "_UNICODE"
    "UNICODE"
)
