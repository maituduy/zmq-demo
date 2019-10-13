cmake_minimum_required(VERSION 3.10)
project(hwserver)

include_directories(include)

## use the hint from above to find where 'zmq.hpp' is located
#find_path(ZeroMQ_INCLUDE_DIR
#        NAMES zmq.hpp
#        PATHS include
#        )

## use the hint from about to find the location of libzmq
find_library(ZeroMQ_LIBRARY
        NAMES zmq
        PATHS "/usr/local/lib"
        )

set (HWSERVER_HEADERS
    include/zmq.hpp
    include/zmq_addon.hpp
)
    
set (HWSERVER_SOURCES
    hwserver.cpp
)

add_executable(hwserver ${HWSERVER_HEADERS} ${HWSERVER_SOURCES})
target_link_libraries(hwserver ${ZeroMQ_LIBRARY})


