sdk_generate_library()
sdk_library_add_sources(${CHIP}/board.c)
sdk_add_include_directories(${CHIP})

sdk_add_compile_definitions(${BOARD})
string(TOUPPER ${CHIP} CHIPNAME)
sdk_add_compile_definitions(${CHIPNAME})

