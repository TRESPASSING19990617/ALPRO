# ALPRO

## Requirements
To install the required packages:

```bash
cd env
bash install_pkg.sh
```

## Downstream Task Finetuning
  - To finetune on downstream tasks

    ```bash
    cd run_scripts
    bash ft_msrvtt_ret.sh
    ```
    
    可修改ft_msrvtt_ret.sh中使用gpu数量:
    ```bash
    cd ..

    export PYTHONPATH="$PYTHONPATH:$PWD"
    echo $PYTHONPATH

    CONFIG_PATH='config_release/msrvtt_ret.json'

    horovodrun -np 8 python src/tasks/run_video_retrieval.py \ # GPU数量
        --config $CONFIG_PATH \
        --output_dir alpro/finetune/msrvtt_ret/$(date '+%Y%m%d%H%M%S')
    ``` 

## 使用docker容器
  - 1、首先导入alpro容器

    ```bash
    service docker start  #开启docker服务
    docker import < alpro.tar    #导入容器
    ```
    
  - 2、将msrvtt_ret文件夹里的videos文件夹拷进容器，再进入alpro容器

    ```bash
    docker cp ALPRO-main/data/msrvtt_ret/videos alpro:/workspace/ALPRO-main/data/msrvtt_ret #容器里没有数据集，需要从外面拷贝进去
    docker exec -it alpro /bin/bash   #进入容器
    ```
    
  - 3、进入环境并运行程序

    ```bash
    source activate dataenvali
    cd ALPRO-main/run_scripts
    bash ft_msrvtt_ret.sh
    ```
    
  - 4、Ctrl+P+Q退出容器，但不关闭容器
