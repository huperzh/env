cmake_minimum_required(VERSION 3.16)

project(env VERSION 0.1 LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release CACHE STRING "Build type" FORCE)
endif()


find_package(QT NAMES Qt5 REQUIRED COMPONENTS Widgets)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Widgets)

set(PROJECT_SOURCES
    main.cpp
    mainwindow.cpp
    mainwindow.h
    mainwindow.ui
)

add_executable(env ${PROJECT_SOURCES})

target_link_libraries(env PRIVATE Qt${QT_VERSION_MAJOR}::Widgets)

set_target_properties(env PROPERTIES
    WIN32_EXECUTABLE TRUE
)

install(TARGETS env
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)
