project(jars-compile-options-public
    VERSION 0.0
    LANGUAGES CXX
)

add_library(jars-compile-options-public
    INTERFACE
)

add_library(jars::compile-options-public
    ALIAS
        jars-compile-options-public
)

if (MSVC)
    target_compile_options(jars-compile-options-public
        INTERFACE
            /Oi         # Enable intrinsic functions
            /std:c++17  # Enable C++ 17 features
    )
elseif (UNIX)
    target_compile_options(jars-compile-options-public
        INTERFACE
            -std=c++17
    )
endif()

install(
    TARGETS
        jars-compile-options-public
    EXPORT
        JarsCompileOptionsPublicTargets
)

install(
    EXPORT
        JarsCompileOptionsPublicTargets
    FILE
        JarsCompileOptionsPublicTargets.cmake
    NAMESPACE
        jars::
    DESTINATION
        lib/cmake/JarsCompileOptionsPublicTargets
)
