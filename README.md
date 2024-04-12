# 1.编译容器
sudo pull registry.baidubce.com/paddlepaddle/paddle:2.6.1-gpu-cuda11.2-cudnn8.2-trt8.0

sudo docker run --name fast_complie -it -v /home/xingyu/work:/home --runtime=nvidia --gpus all --privileged=true registry.baidubce.com/paddlepaddle/paddle:2.6.1-gpu-cuda11.2-cudnn8.2-trt8.0
python=3.10
pip install wheel
apt-get install python3-dev
apt-get install cmake

# 2.python api 编译方式  
不使用TRT,OPENVINO 只用 paddle，onnx。
vim ~/.bashrc
export ENABLE_ORT_BACKEND=ON
export ENABLE_PADDLE_BACKEND=ON
export ENABLE_VISION=ON
export ENABLE_TEXT=ON
export WITH_GPU=ON
export CUDA_DIRECTORY=/usr/local/cuda-11.2

source ~/.bashrc

python setup.py build

python setup.py bdist_wheel


# 3.环境配置:
不支持 paddle2.6.2 


如果需要 paddle 
pip install paddlepaddle-gpu==2.5.2.post112 -f https://www.paddlepaddle.org.cn/whl/linux/mkl/avx/stable.html
如果需要

pip install "paddleocr>=2.0.1"
conda config --add channels conda-forge && conda install cudatoolkit=11.2 cudnn=8.2

如果用官方的
pip install fastdeploy-gpu-python==0.0.0 -f https://www.paddlepaddle.org.cn/whl/fastdeploy_nightly_build.html

