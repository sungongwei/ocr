已测试环境
- ubantu20.04
  - python3.8
  - cpu
    - 响应速度0.1-3s
  - gpu a10
  -  0.1-1
## 安装依赖
### CPU
  - python3.8

`./install`
### GPU
 - python3.8
 - cuda11.2
 - cudnn8.1.1
  
`./install_gpu`
## 启动服务
### 参数配置
cpu使用v3_lite模型

  `config.yml`
### 启动
`./start.sh`
## 测试接口
`../test`

## 接口
- url 
  - http://127.0.0.1:9998/ocr/prediction
- method
  - post
- data
  - image :base64()