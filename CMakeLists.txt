cmake_minimum_required(VERSION 2.7)
project(lab3)


find_package(MPI REQUIRED)
include_directories(${MPI_INCLUDE_PATH})

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O3 -lm")

add_executable(sieve0 sieve0.c)
add_executable(sieve1 sieve1.c)
add_executable(sieve2 sieve2.c)
add_executable(sieve3 sieve3.c)

set(TARGET_LIST "sieve0 sieve1 sieve2 sieve3")

target_link_libraries(sieve0 ${MPI_LIBRARIES})
target_link_libraries(sieve1 ${MPI_LIBRARIES})
target_link_libraries(sieve2 ${MPI_LIBRARIES})
target_link_libraries(sieve3 ${MPI_LIBRARIES})

if(MPI_COMPILE_FLAGS)
  set_target_properties(sieve0 PROPERTIES
    COMPILE_FLAGS "${MPI_COMPILE_FLAGS}")
  set_target_properties(sieve1 PROPERTIES
    COMPILE_FLAGS "${MPI_COMPILE_FLAGS}")
  set_target_properties(sieve2 PROPERTIES
    COMPILE_FLAGS "${MPI_COMPILE_FLAGS}")
  set_target_properties(sieve3 PROPERTIES
    COMPILE_FLAGS "${MPI_COMPILE_FLAGS}")
endif()

if(MPI_LINK_FLAGS)
  set_target_properties(sieve0 PROPERTIES
    LINK_FLAGS "${MPI_LINK_FLAGS}")
  set_target_properties(sieve1 PROPERTIES
    LINK_FLAGS "${MPI_LINK_FLAGS}")
  set_target_properties(sieve2 PROPERTIES
    LINK_FLAGS "${MPI_LINK_FLAGS}")
  set_target_properties(sieve3 PROPERTIES
    LINK_FLAGS "${MPI_LINK_FLAGS}")
endif()
