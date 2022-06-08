sdk_generate_library()

file(GLOB_RECURSE sources
"${CMAKE_CURRENT_SOURCE_DIR}/*.c"
)

sdk_library_add_sources(${sources})
sdk_add_include_directories(memheap)
sdk_add_include_directories(misc)
sdk_add_include_directories(list)
sdk_add_include_directories(device)
sdk_add_include_directories(soft_crc)
sdk_add_include_directories(ring_buffer)
