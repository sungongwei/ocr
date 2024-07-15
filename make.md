apt install -y golang  patchelf libssl-dev

#for av
apt install -y libavformat-dev libavcodec-dev libavdevice-dev libavutil-dev libswscale-dev libavresample-dev libavfilter-dev libopenmpi-dev


git clone https://github.com/PaddlePaddle/Serving
cd Serving && git submodule update --init --recursive

# Paddle开发镜像需要运行如下命令，Serving开发镜像不需要运行
bash tools/paddle_env_install.sh


find / -name Python.h
find / -name libpython3.8.so
which python3.8


### TODO 
export PYTHON_INCLUDE_DIR=/opt/conda/include/python3.8/
export PYTHON_LIBRARIES=/usr/lib/python3.8/config-3.8-x86_64-linux-gnu/libpython3.8.so
export PYTHON_EXECUTABLE=/opt/conda/bin/python3.8
export CUDA_PATH='/usr/local/cuda'
export CUDNN_LIBRARY='/usr/local/cuda/lib64/'
export CUDA_CUDART_LIBRARY="/usr/local/cuda/lib64/"
export TENSORRT_LIBRARY_PATH="/usr/"

```
python3.7 -m pip install -r python/requirements.txt
 ```
 ```
go env -w GO111MODULE=on
go env -w GOPROXY=https://goproxy.cn,direct
go install github.com/grpc-ecosystem/grpc-gateway/protoc-gen-grpc-gateway@v1.15.2
go install github.com/grpc-ecosystem/grpc-gateway/protoc-gen-swagger@v1.15.2
go install github.com/golang/protobuf/protoc-gen-go@v1.4.3
go install google.golang.org/grpc@v1.33.0
go env -w GO111MODULE=auto
```

```
mkdir build_server
cd build_server
cmake -DPYTHON_INCLUDE_DIR=$PYTHON_INCLUDE_DIR \
    -DPYTHON_LIBRARIES=$PYTHON_LIBRARIES \
    -DPYTHON_EXECUTABLE=$PYTHON_EXECUTABLE \
    -DCUDA_TOOLKIT_ROOT_DIR=${CUDA_PATH} \
    -DCUDNN_LIBRARY=${CUDNN_LIBRARY} \
    -DCUDA_CUDART_LIBRARY=${CUDA_CUDART_LIBRARY} \
    -DTENSORRT_ROOT=${TENSORRT_LIBRARY_PATH} \
    -DSERVER=ON \
    -DWITH_GPU=ON ..
make -j20
cd ..
```

pip install build_server/python/dist/*.whl