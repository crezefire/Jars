if (JARS_ENABLE_BENCHMARKING)
    add_subdirectory(benchmarks)
    set_property(TARGET jars-benchmarks PROPERTY FOLDER "src")
endif()

if (JARS_ENABLE_TESTING)
    add_subdirectory(tests)
    set_property(TARGET jars-tests PROPERTY FOLDER "src")
endif()
