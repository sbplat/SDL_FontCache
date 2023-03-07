cmake_minimum_required(VERSION 3.1)
project(
  SDL_FontCache
  VERSION 0.10.0
  LANGUAGES C)

include(FindPkgConfig)

pkg_search_module(SDL2 REQUIRED sdl2)
pkg_search_module(SDL2_TTF REQUIRED SDL2_ttf)

add_library(FontCache SDL_FontCache.h SDL_FontCache.c)

target_include_directories(FontCache PUBLIC ${SDL2_INCLUDE_DIRS}
                                            ${SDL2_TTF_INCLUDE_DIRS})

target_link_libraries(FontCache PUBLIC ${SDL2_LIBRARIES} ${SDL2_TTF_LIBRARIES})

add_executable(FontCache-tests test/main.c)

target_include_directories(
  FontCache-tests PRIVATE ${CMAKE_CURRENT_SOURCE_DIR} ${SDL2_INCLUDE_DIRS}
                          ${SDL2_TTF_INCLUDE_DIRS})

target_link_libraries(FontCache-tests PRIVATE FontCache)

file(COPY test/utf8_sample.txt DESTINATION ${CMAKE_BINARY_DIR})
file(COPY test/fonts/FreeSans.ttf DESTINATION ${CMAKE_BINARY_DIR}/fonts)
