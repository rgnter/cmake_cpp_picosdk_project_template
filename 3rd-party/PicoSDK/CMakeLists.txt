
set(PICO_SDK_FETCH_FROM_GIT on)
if(NOT EXISTS $ENV{PICO_SDK_PATH})
    message("PicoSDK is not available")
else()
    include($ENV{PICO_SDK_PATH}/pico_sdk_init.cmake)
endif()