project(jars-benchmarks
    VERSION 0.0
    LANGUAGES CXX
)

add_executable(jars-benchmarks
    ${CMAKE_CURRENT_SOURCE_DIR}/main.cpp
)

add_executable(jars::jars-benchmarks
    ALIAS
        jars-benchmarks
)

target_link_libraries(jars-benchmarks
    INTERFACE
        jars::compile-options-private
)

if (MSVC)
    target_link_libraries(jars-benchmarks
        PRIVATE
            jars::ext_google_benchmark $<$<CONFIG:Release>:-LTCG>
    )
else()
    target_link_libraries(jars-benchmarks
        PRIVATE
            jars::ext_google_benchmark
    )
endif()
