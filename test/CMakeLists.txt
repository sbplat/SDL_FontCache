add_executable(FontCacheTest main.c)

set(PLATFORM_DEPENDENT_LIBS "")
if(UNIX)
  set(PLATFORM_DEPENDENT_LIBS ${PLATFORM_DEPENDENT_LIBS} m)
endif()

target_link_libraries(FontCacheTest FontCache ${PLATFORM_DEPENDENT_LIBS})

target_include_directories(FontCacheTest PRIVATE ${FontCache_INCLUDE_DIRS})

file(COPY ${CMAKE_CURRENT_SOURCE_DIR}/utf8_sample.txt
     DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
file(COPY ${CMAKE_CURRENT_SOURCE_DIR}/fonts/FreeSans.ttf
     DESTINATION ${CMAKE_CURRENT_BINARY_DIR}/fonts)
