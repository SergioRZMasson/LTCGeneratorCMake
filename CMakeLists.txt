cmake_minimum_required(VERSION 3.21)
project(LTCGenerator)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(LTC_GENERATOR_SOURCE
    "Dependencies/ltc_code/fit/dds.cpp"
    "src/main.cpp")

set(LTC_GENERATOR_HEADERS
    "Dependencies/ltc_code/fit/brdf_beckmann.h"
    "Dependencies/ltc_code/fit/brdf_disneyDiffuse.h"
    "Dependencies/ltc_code/fit/brdf_ggx.h"
    "Dependencies/ltc_code/fit/brdf.h"
    "Dependencies/ltc_code/fit/dds.h"
    "Dependencies/ltc_code/fit/export.h"
    "Dependencies/ltc_code/fit/float_to_half.h"
    "Dependencies/ltc_code/fit/LTC.h"
    "Dependencies/ltc_code/fit/nelder_mead.h"
    "Dependencies/ltc_code/fit/plot.h")

add_executable(LTCGenerator ${LTC_GENERATOR_SOURCE} ${LTC_GENERATOR_HEADERS})
target_include_directories(LTCGenerator PRIVATE "src")
target_include_directories(LTCGenerator PRIVATE "Dependencies/ltc_code/fit/")

if(DEFINED EMSCRIPTEN)
    target_link_options(LTCGenerator PRIVATE "-s EXPORTED_FUNCTIONS=['BuildLTC', 'my_malloc', 'my_free']" "-s EXPORTED_RUNTIME_METHODS=['cwrap', 'allocate', 'ALLOC_NORMAL']" "-s NO_EXIT_RUNTIME=1")
    target_link_options(LTCGenerator PRIVATE -s EXPORT_NAME="LTCGenerator")
endif()

find_package(glm CONFIG REQUIRED)
target_link_libraries(LTCGenerator PUBLIC glm::glm)

find_package(CImg CONFIG REQUIRED)
target_link_libraries(LTCGenerator PUBLIC CImg::CImg)