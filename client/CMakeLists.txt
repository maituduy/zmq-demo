cmake_minimum_required(VERSION 3.10)
project(hwclient)

include_directories(include "C:/Program Files (x86)/ZeroMQ/include")

## use the hint from above to find where 'zmq.hpp' is located
#find_path(ZeroMQ_INCLUDE_DIR
#        NAMES zmq.hpp
#        PATHS include
#        )

## use the hint from about to find the location of libzmq
find_library(ZeroMQ_LIBRARY
        NAMES zmq
        PATHS "C:/Program Files (x86)/ZeroMQ/bin"
        )

set (HWCLIENT_HEADERS
    include/zmq.hpp
    include/zmq_addon.hpp
)

set (HWCLIENT_SOURCES
    hwclient.cpp
)

add_executable(hwclient ${HWCLIENT_HEADERS} ${HWCLIENT_SOURCES})
target_link_libraries(hwclient ${ZeroMQ_LIBRARY})


