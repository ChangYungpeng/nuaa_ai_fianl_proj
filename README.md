本项目为NUAA，AI课设代码。

项目安装：

```shell
pip install -r requirements.txt
```

微调：

```shell
CUDA_VISIBLE_DEVICES=0 python src/train_bash.py \
    --stage sft \
    --model_name_or_path path_to_chatglm \
    --do_train \
    --dataset dianli \
    --template default \
    --finetuning_type lora \
    --lora_target query_key_value \
    --output_dir path_to_checkpoint \
    --overwrite_cache \
    --per_device_train_batch_size 4 \
    --gradient_accumulation_steps 4 \
    --lr_scheduler_type cosine \
    --logging_steps 10 \
    --save_steps 1000 \
    --learning_rate 5e-5 \
    --num_train_epochs 3.0 \
    --plot_loss
```

测试：

```shell
CUDA_VISIBLE_DEVICES=0 python src/cli_demo.py \
    --model_name_or_path path_to_chatglm \
    --template default \
    --finetuning_type lora \
    --checkpoint_dir path_to_checkpoint
```

