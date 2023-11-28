# iTransformer for Multivariate Time Series Forecasting

This folder contains the implementation of the iTransformer for Multivariate Time Series Forecasting (MTSF).

## Dataset

Six challenging multivariate forecasting tasks are evaluated as the benchmark. We provide the download links: [Google Drive](https://drive.google.com/file/d/1l51QsKvQPcqILT3DwfjCgx8Dsg2rpjot/view?usp=drive_link) or [Tsinghua Cloud](https://cloud.tsinghua.edu.cn/f/2ea5ca3d621e4e5ba36a/).

<p align="center">
<img src="../..//figures/datasets_mtsf.png" alt="" align=center />
</p>

## Scripts

In each folder named after the dataset, we provide the iTransformer experiments under four different prediction lengths as shown in the table above.
在每个以数据集命名的文件夹中，我们提供了上表所示四种不同预测长度下的 iTransformer 实验。
```
# iTransformer on the Traffic Dataset

bash ./scripts/multivariate_forecast/Traffic/iTransformer.sh
```

To evaluate the model under other input/prediction length, feel free to change the ```seq_len``` and ```pred_len``` arguments:
要评估其他输入/预测长度下的模型，请随意更改 seq_len 和 pred_len 参数：
```
# iTransformer on the Electricity Dataset, where 180 time steps are inputed as the observations and the task is to predict the future 60 steps

python -u run.py \
  --is_training 1 \
  --root_path ./dataset/electricity/ \
  --data_path electricity.csv \
  --model_id ECL_180_60 \
  --model $model_name \
  --data custom \
  --features M \
  --seq_len 180 \
  --pred_len 60 \
  --e_layers 3 \
  --enc_in 321 \
  --dec_in 321 \
  --c_out 321 \
  --des 'Exp' \
  --d_model 512 \
  --d_ff 512 \
  --batch_size 16 \
  --learning_rate 0.0005 \
  --itr 1
```


## Training on Custom Dataset
自定义数据集培训
To train with your own time series dataset, you can try out the following steps:
要使用自己的时间序列数据集进行训练，可以尝试以下步骤：
1. Read through the ```Dataset_Custom``` class under the ```data_provider/data_loader``` folder, which provides the functionality to load and process time series files.阅读 ```data_provider/data_loader``` 文件夹下的 ```Dataset_Custom``` 类，该类提供加载和处理时间序列文件的功能。
2. The file should be ```csv``` format with the first column contains the timestamp and the following columns contain the variates of time series.
文件应为```csv```格式，第一列包含时间戳，以下各列包含时间序列的变量。
3. Set ```data=custom``` and modifiy the ```enc_in```, ```dec_in```, ```c_out``` arguments acoording to your number of variates in the training script.
设置 ```data=custom``` 并根据训练脚本中的变量数量修改 ``enc_in```、``dec_in```、``c_out`` 参数。
