cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project(TorchExample)
#set(CUDA_TOOLKIT_ROOT_DIR /usr/local/cuda)
set(Torch_DIR /home/kwoodle/src/libtorch/share/cmake/Torch)
find_package(Torch REQUIRED)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${TORCH_CXX_FLAGS}")
include(/usr/local/lib/ktrade/cmake/ktrade-targets.cmake)

add_executable(mnist mnist.cpp)
set_property(TARGET mnist PROPERTY CXX_STANDARD 14)
target_link_libraries(mnist Ktrd "${TORCH_LIBRARIES}")
add_executable(dcgan dcgan.cpp)
set_property(TARGET dcgan PROPERTY CXX_STANDARD 14)
target_link_libraries(dcgan Ktrd "${TORCH_LIBRARIES}")

