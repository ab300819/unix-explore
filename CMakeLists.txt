cmake_minimum_required(VERSION 3.5.1)
project(unix_programming CXX C)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 20)

message(STATUS ${CMAKE_SYSTEM_NAME})
if (CMAKE_SYSTEM_NAME MATCHES "Linux")
	set(APUE /home/zeus/apue.3e)
    # set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread")
elseif (CMAKE_SYSTEM_NAME MATCHES "Darwin")
	set(APUE /Users/mason/Project/book_source/unix/apue.3e)
endif ()

include_directories(${APUE}/include)
link_directories(${APUE}/lib)

# c primer plus
add_executable(main src/main.c)

# unix apue
add_executable(apue_main src/apue/1_3.c)
target_link_libraries(apue_main apue)

# unix unp
add_executable(unp_main src/unp/main.c)

add_executable(server src/geek_time/server.c)
add_executable(client src/geek_time/client.c)