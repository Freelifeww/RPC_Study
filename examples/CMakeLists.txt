cmake_minimum_required(VERSION 3.1)
project(example)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread -std=c++11")

SET(ENABLE_SSL OFF)

if (ENABLE_SSL)
    add_definitions(-DCINATRA_ENABLE_SSL)
    message(STATUS "Use SSL")
endif()

#find_package(Boost COMPONENTS system filesystem REQUIRED)
#find_package(JNI REQUIRED)

# include_directories(
#         "/usr/local/include"
#         "../include"
#         "../thirdparty/msgpack-c/include")

include_directories(
        "../include"
        "../thirdparty/msgpack-c/include")

add_executable(basic_server server/main.cpp)
add_executable(basic_client client/main.cpp)

# if (ENABLE_SSL)
#     target_link_libraries(basic_server ${Boost_LIBRARIES} -lssl -lcrypto -lpthread)
#     target_link_libraries(basic_client ${Boost_LIBRARIES} -lssl -lcrypto -lpthread)
# else()
#     target_link_libraries(basic_server ${Boost_LIBRARIES})
#     target_link_libraries(basic_client ${Boost_LIBRARIES})
# endif()
