cmake_minimum_required(VERSION 3.0.0)
project(flash_tool VERSION 0.1.0 LANGUAGES C)

include_directories(inc)

set(PROJECT_SOURCES
            src/mtk_da.c
            src/mtk_device.c
            src/mtk_preloader.c
            src/util.h

            inc/mtk_da.h
            inc/mtk_device.h
            inc/mtk_preloader.h

            flash_tool/args.c
            flash_tool/args.h
            flash_tool/io_handler.c
            flash_tool/io_handler.h
            flash_tool/main.c
            flash_tool/util.c
            flash_tool/util.h
)

add_executable(flash_tool ${PROJECT_SOURCES})
target_include_directories(flash_tool PRIVATE ${PROJECT_SOURCE_DIR})
target_link_libraries(flash_tool PRIVATE usb-1.0)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
