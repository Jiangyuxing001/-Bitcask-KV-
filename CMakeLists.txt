cmake_minimum_required(VERSION 3.16)

project(alphaDB)

set(CMAKE_CXX_STANDARD 11)

include_directories(./inc)

file(GLOB SRC ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cc)

link_directories(${CMAKE_CURRENT_SOURCE_DIR}/lib)

find_package(ZLIB REQUIRED)

set(
    LIB_LIB
    pthread
    alpha
    ZLIB::ZLIB    
)

# add_executable(test_file_io tests/test_file_io.cc ${SRC})
# target_link_libraries(test_file_io ${LIB_LIB}) 

# add_executable(test_data_file tests/test_data_file.cc ${SRC})
# target_link_libraries(test_data_file ${LIB_LIB}) 

# add_executable(test_log_record tests/test_log_record.cc ${SRC})
# target_link_libraries(test_log_record ${LIB_LIB}) 

# add_executable(test_db tests/test_db.cc ${SRC})
# target_link_libraries(test_db ${LIB_LIB}) 

# add_executable(test_map tests/test_map.cc ${SRC})
# target_link_libraries(test_map ${LIB_LIB}) 

# add_executable(test_iterator tests/test_iterator.cc ${SRC})
# target_link_libraries(test_iterator ${LIB_LIB}) 

# add_executable(test_batch tests/test_batch.cc ${SRC})
# target_link_libraries(test_batch ${LIB_LIB}) 

add_executable(test_merge tests/test_merge.cc ${SRC})
target_link_libraries(test_merge ${LIB_LIB}) 

add_executable(test_flock tests/test_flock.cc ${SRC})
target_link_libraries(test_flock ${LIB_LIB}) 

SET(EXECUTABLE_OUTPUT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/bin)
SET(CMAKE_BUILD_TYPE "Debug")  # 定义编译类型
SET(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -O0 -g2 -ggdb") # 定义Debug编译参数
SET(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS} -O3 -Wall") # 定义Release编译参数