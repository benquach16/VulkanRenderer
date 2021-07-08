set (CMAKE_EXPORT_COMPILE_COMMANDS 1)
set (CMAKE_CXX_STANDARD 17)
set (CMAKE_BUILD_TYPE Debug)
set( MAKE_CXX_FLAGS "-g -Werror -Wold-style-cast -Wpedantic" )

cmake_minimum_required (VERSION 2.8.11)
project (Renderer)

set(SOURCES
    ./src/main.cpp)
set(DIRS
    ./src)
add_executable(Renderer ${SOURCES})

if(WIN32)
    set(SFML_DIR "C:/SFML-2.5.1/lib/cmake/SFML")
    set(SFML_ROOT "C:/SFML-2.5.1")
endif()

if(SFML_FOUND)
    include_directories(${SFML_INCLUDE_DIR})
    include_directories(${DIRS})
    target_link_libraries(RPG sfml-graphics sfml-window sfml-system)    
    message("\n found SFML")
else()
    message("\n could not find SFML")
endif()
