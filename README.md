# ALPRO

## Requirements
To install the required packages:

```bash
cd env && bash install_pkg.sh
```

## Downstream Task Finetuning
  - To finetune on downstream tasks with the pre-trained checkpoint `output/pretrain/alpro_pretrained_ckpt.pt`

    ```bash
    cd run_scripts
    bash ft_msrvtt_ret.sh
    bash ft_didemo_ret.sh
    bash ft_msrvtt_qa.sh
    bash ft_msvd_qa.sh
    ```
