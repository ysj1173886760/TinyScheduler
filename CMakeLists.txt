cmake_minimum_required(VERSION 3.14)
project(TinyThread)

set(CMAKE_CXX_STANDARD 17)              # Compile as C++17
set(CMAKE_CXX_STANDARD_REQUIRED ON)     # Require C++17 support

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -ggdb -fPIC -Wall -Wextra -fno-stack-protector -march=native")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -O0 -ggdb -fsanitize=address -fno-omit-frame-pointer -fno-optimize-sibling-calls -fno-stack-protector")

message(STATUS "CMAKE_CXX_FLAGS: ${CMAKE_CXX_FLAGS}")
message(STATUS "CMAKE_CXX_FLAGS_DEBUG: ${CMAKE_CXX_FLAGS_DEBUG}")

include_directories(${PROJECT_SOURCE_DIR}/src)

add_executable(TinyThread src/adeque.cpp 
                          src/coroutine.cpp 
                          src/master.cpp
                          src/main.cpp)

target_link_libraries(TinyThread pthread)