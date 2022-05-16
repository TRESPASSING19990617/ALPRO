# ALPRO

## Requirements
To install the required packages:

```bash
cd env && bash install_pkg.sh
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
        --output_dir /export/home/workspace/experiments/alpro/finetune/msrvtt_ret/$(date '+%Y%m%d%H%M%S')  # change to your local path to store finetuning ckpts and logs 
    ``` 
