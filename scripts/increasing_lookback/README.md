# iTransformer for Enlarged Lookback Window

This folder contains the implementation of the iTransformer for enlarged lookback window. If you are new to this repo, we recommend you to read this [README](../multivariate_forecast/README.md) first.该文件夹包含用于放大回视窗口的 iTransformer 的实现。如果您是新手，建议您先阅读 README。

## Scripts

In each folder named after the dataset, we provide the iTransformers and the vanilla Transformers experiments under four five increasing prediction lengths.在每个以数据集命名的文件夹中，我们提供了在四种五种增加预测长度下的iTransformer和普通Transformer实验

```
# iTransformer on the Traffic Dataset with gradually enlarged lookback windows.

bash ./scripts/increasing_lookback/Traffic/iTransformer.sh
```

You can change the ```model_name``` in the script to switch the selection of the vanilla Transformer and inverted version.

## Results

<p align="center">
<img src="../../figures/increase_lookback.png" alt="" align=center />
</p>

The inverted framework empowers Transformers with improved performance on the enlarged lookback window.
