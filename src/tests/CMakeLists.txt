project(jars-tests
    VERSION 0.0
    LANGUAGES CXX
)

add_executable(jars-tests
    ${CMAKE_CURRENT_SOURCE_DIR}/main.cpp
)

add_executable(jars::jars-tests
    ALIAS
        jars-tests
)

target_link_libraries(jars-tests
    INTERFACE
        jars::compile-options-private
    PRIVATE
        jars::ext_google_test
)
