set(LTC_GENERATOR_EMSCRIPTEN_GLUB_SOURCE
    "src/main.cpp")

add_executable(LTCGeneratorLibEmscriptenGlue ${LTC_GENERATOR_EMSCRIPTEN_GLUB_SOURCE})

target_link_libraries(LTCGeneratorLibEmscriptenGlue PUBLIC LTCGeneratorLib)
target_include_directories(LTCGeneratorLibEmscriptenGlue PUBLIC "src")

target_compile_definitions(LTCGeneratorLibEmscriptenGlue PRIVATE "EXPORTED_RUNTIME_METHODS=['ccall']" "NO_EXIT_RUNTIME=1")