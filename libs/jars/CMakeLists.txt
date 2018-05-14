project(jars
    VERSION 0.0
    LANGUAGES CXX
)

add_library(jars
    STATIC
        ${CMAKE_CURRENT_SOURCE_DIR}/src/engine.cpp
)

add_library(jars::jars
    ALIAS
        jars
)

target_include_directories(jars
    PUBLIC
        $<BUILD_INTERFACE:${jars_BINARY_DIR}/include>
        $<BUILD_INTERFACE:${jars_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:include>
)

target_link_libraries(jars
    PRIVATE
        jars::compile-options-private
    PUBLIC
        jars::compile-options-public
)

install(
    TARGETS
        jars
    EXPORT
        JarsTargets
    LIBRARY DESTINATION
        lib
    ARCHIVE DESTINATION
        lib
    RUNTIME DESTINATION
        bin
    INCLUDES DESTINATION
        include
    PUBLIC_HEADER DESTINATION
        include
)

install(
    DIRECTORY
        include/
    DESTINATION
        include
)

install(
    EXPORT
        JarsTargets
    FILE
        JarsTargets.cmake
    NAMESPACE
        jars::
    DESTINATION
        lib/cmake/jars
)

include(CMakePackageConfigHelpers)

write_basic_package_version_file(
    "JarsConfigVersion.cmake"
    VERSION
        ${jars_VERSION}
    COMPATIBILITY
        SameMajorVersion
)

install(
    FILES
        "JarsConfig.cmake"
        "${CMAKE_CURRENT_BINARY_DIR}/JarsConfigVersion.cmake"
    DESTINATION
        lib/cmake/jars
)

export(
    PACKAGE
        jars
)
