nvcc = /usr/local/cuda-10.0/bin/nvcc
cudalib = /usr/local/cuda-10.0/lib64/
tensorflow = /opt/anaconda3/envs/thesis/lib/python3.7/site-packages/tensorflow/include

all: tf_nndistance_so.so render_balls_so.so
.PHONY : all

tf_nndistance_so.so: tf_nndistance_g.cu.o tf_nndistance.cpp
	g++ -std=c++11 tf_nndistance.cpp tf_nndistance_g.cu.o -o tf_nndistance_so.so -shared -fPIC -I $(tensorflow) -lcudart -L $(cudalib) -O2 

tf_nndistance_g.cu.o: tf_nndistance_g.cu
	$(nvcc) -std=c++11 -c -o tf_nndistance_g.cu.o tf_nndistance_g.cu -I $(tensorflow) -DGOOGLE_CUDA=1 -x cu -Xcompiler -fPIC -O2

render_balls_so.so: render_balls_so.cpp
	g++ -std=c++11 render_balls_so.cpp -o render_balls_so.so -shared -fPIC -O2


