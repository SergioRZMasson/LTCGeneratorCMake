set(LTC_GENERATOR_APP_SOURCE 
    "../Dependencies/ltc_code/fit/fitLTC.cpp")

add_executable(LTCGeneratorApp ${LTC_GENERATOR_APP_SOURCE})
target_link_libraries(LTCGeneratorApp PUBLIC LTCGeneratorLib)
