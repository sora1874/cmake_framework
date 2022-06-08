file(GLOB_RECURSE sources
"${CMAKE_CURRENT_SOURCE_DIR}/std_drv/src/*.c"
"${CMAKE_CURRENT_SOURCE_DIR}/hal_drv/src/*.c"
"${CMAKE_CURRENT_SOURCE_DIR}/startup/interrupt.c"
"${CMAKE_CURRENT_SOURCE_DIR}/startup/system_bl702.c"
"${CMAKE_CURRENT_SOURCE_DIR}/startup/GCC/entry.S"
"${CMAKE_CURRENT_SOURCE_DIR}/startup/GCC/start_load.c"
)
list(APPEND ADD_SRCS  ${sources})
list(REMOVE_ITEM ADD_SRCS "${CMAKE_CURRENT_SOURCE_DIR}/std_drv/src/bl702_snflash.c"
"${CMAKE_CURRENT_SOURCE_DIR}/std_drv/src/bl702_romdriver.c"
)

sdk_generate_library()

sdk_library_add_sources(${ADD_SRCS})
sdk_add_include_directories(
hal_drv/inc
hal_drv/default_config
std_drv/inc
regs
startup
.
)

SET(MCPU "riscv-e24")
SET(MARCH "rv32imafc")
SET(MABI "ilp32f")

sdk_add_compile_definitions(BFLB_USE_HAL_DRIVER ARCH_RISCV BFLB_USE_ROM_DRIVER)
sdk_add_compile_options(-march=${MARCH} -mabi=${MABI})
sdk_add_link_options(-march=${MARCH} -mabi=${MABI})

sdk_set_linker_script(bl702_flash.ld)