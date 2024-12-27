set(LTC_GENERATOR_LIB_SOURCE
    "../Dependencies/ltc_code/fit/dds.cpp")

set(LTC_GENERATOR_LIB_HEADERS
    "../Dependencies/ltc_code/fit/brdf_beckmann.h"
    "../Dependencies/ltc_code/fit/brdf_disneyDiffuse.h"
    "../Dependencies/ltc_code/fit/brdf_ggx.h"
    "../Dependencies/ltc_code/fit/brdf.h"
    "../Dependencies/ltc_code/fit/dds.h"
    "../Dependencies/ltc_code/fit/export.h"
    "../Dependencies/ltc_code/fit/float_to_half.h"
    "../Dependencies/ltc_code/fit/LTC.h"
    "../Dependencies/ltc_code/fit/nelder_mead.h"
    "../Dependencies/ltc_code/fit/plot.h")

add_library(LTCGeneratorLib ${LTC_GENERATOR_LIB_SOURCE} ${LTC_GENERATOR_LIB_HEADERS})

find_package(glm CONFIG REQUIRED)
target_link_libraries(LTCGeneratorLib PUBLIC glm::glm)

find_package(CImg CONFIG REQUIRED)
target_link_libraries(LTCGeneratorLib PUBLIC CImg::CImg)

target_include_directories(LTCGeneratorLib PUBLIC "../Dependencies/ltc_code/fit/")