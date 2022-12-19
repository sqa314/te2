cmake_minimum_required(VERSION 3.16)

project(untitled1fff VERSION 0.1 LANGUAGES CXX)

set(CMAKE_AUTOMOC ON)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_STATIC_LINKER_FLAGs "-static")
set(QT_STATIC PLUGIN TRUE)
set(CMAKE_EXE_LINKER_FLAGS "-static-libgcc -static-libstdc++")
find_package(Qt6 6.2 COMPONENTS Quick REQUIRED)

qt_add_executable(appuntitled1fff
    main.cpp
)

qt_add_qml_module(appuntitled1fff
    URI untitled1fff
    VERSION 1.0
    QML_FILES main.qml 
)

set_target_properties(appuntitled1fff PROPERTIES
    MACOSX_BUNDLE_GUI_IDENTIFIER my.example.com
    MACOSX_BUNDLE_BUNDLE_VERSION ${PROJECT_VERSION}
    MACOSX_BUNDLE_SHORT_VERSION_STRING ${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}
    MACOSX_BUNDLE TRUE
    WIN32_EXECUTABLE TRUE
)

target_link_libraries(appuntitled1fff
    PRIVATE Qt6::Quick)

install(TARGETS appuntitled1fff
    BUNDLE DESTINATION .
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR})
