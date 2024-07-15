已测试环境
ubantu22.04
  python3.8
  0.2-3
## 安装依赖
### CPU
`./install`
### GPU
`./install_gpu`
## 启动服务
### 参数配置
  `config.yml`

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