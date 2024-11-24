#cmake的最小版本
cmake_minimum_required(VERSION 3.2)

project(main)

#寻找torch
find_package(Torch PATHS "/media/zzh/data/lib/anaconda3/envs/gym/lib/python3.8/site-packages/torch/share/cmake/Torch/" REQUIRED)

#寻找pybind
find_package(pybind11 PATHS "/media/zzh/data/lib/anaconda3/envs/gym/lib/python3.8/site-packages/pybind11/share/cmake/pybind11/" REQUIRED)

include_directories(./include)
include_directories(/media/zzh/data/lib/anaconda3/envs/gym/include/python3.8/)

add_library(bvh 
./src/bvh.cu
./src/construct.cu
./src/trace.cu)

target_link_libraries(bvh ${TORCH_LIBRARIES})

