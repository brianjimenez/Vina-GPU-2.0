# Need to be modified according to different users
# On Ubuntu, run first: apt install libboost-all-dev libthread-pool-dev
BOOST_LIB_PATH=/usr/include/boost
OPENCL_LIB_PATH=/usr/local/cuda-12
OPENCL_VERSION=-DOPENCL_2_0
GPU_PLATFORM=-DNVIDIA_PLATFORM

# Should not be modified
BOOST_INC_PATH=-I$(BOOST_LIB_PATH) -I$(BOOST_LIB_PATH)/boost 
VINA_GPU_INC_PATH=-I./lib -I./OpenCL/inc 
OPENCL_INC_PATH=-I$(OPENCL_LIB_PATH)/include
LIB1=-lboost_program_options -lboost_system -lboost_filesystem -lOpenCL
LIB2=-lstdc++ -lstdc++fs
LIB3=-lm -lboost_thread -lpthread
LIB_PATH=-L$(BOOST_LIB_PATH)/stage/lib -L$(OPENCL_LIB_PATH)/lib64
SRC=./lib/*.cpp ./OpenCL/src/wrapcl.cpp $(BOOST_LIB_PATH)/thread/thread.hpp $(BOOST_LIB_PATH)/thread/once.hpp
MACRO=$(OPENCL_VERSION) $(GPU_PLATFORM) #-DDISPLAY_SUCCESS -DDISPLAY_ADDITION_INFO
all:out
out:./main/main.cpp
	gcc -o Vina-GPU $(BOOST_INC_PATH) $(VINA_GPU_INC_PATH) $(OPENCL_INC_PATH) ./main/main.cpp -O3 $(SRC) $(LIB1) $(LIB2) $(LIB3) $(LIB_PATH) $(MACRO) $(OPTION)
source:./main/main.cpp
	gcc -o Vina-GPU $(BOOST_INC_PATH) $(VINA_GPU_INC_PATH) $(OPENCL_INC_PATH) ./main/main.cpp -O3 $(SRC) $(LIB1) $(LIB2) $(LIB3) $(LIB_PATH) $(MACRO) $(OPTION) -DBUILD_KERNEL_FROM_SOURCE 
debug:./main/main.cpp
	gcc -o Vina-GPU $(BOOST_INC_PATH) $(VINA_GPU_INC_PATH) $(OPENCL_INC_PATH) ./main/main.cpp -g $(SRC) $(LIB1) $(LIB2) $(LIB3) $(LIB_PATH) $(MACRO) $(OPTION) -DBUILD_KERNEL_FROM_SOURCE 
clean:
	rm Vina-GPU
