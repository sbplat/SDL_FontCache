add_executable(FontCacheTest main.c)

target_link_libraries(FontCacheTest FontCache)

target_include_directories(FontCacheTest PRIVATE ${FontCache_INCLUDE_DIRS})

file(COPY ${CMAKE_CURRENT_SOURCE_DIR}/utf8_sample.txt
     DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
file(COPY ${CMAKE_CURRENT_SOURCE_DIR}/fonts/FreeSans.ttf
     DESTINATION ${CMAKE_CURRENT_BINARY_DIR}/fonts)
