project(tests
    VERSION 0.0
    LANGUAGES CXX
)

add_executable(tests
    ${CMAKE_CURRENT_SOURCE_DIR}/main.cpp
)

add_executable(jars::tests
    ALIAS
        tests
)

target_link_libraries(tests
    INTERFACE
        jars::compile-options-private
    PRIVATE
        jars::ext_google_test
)
