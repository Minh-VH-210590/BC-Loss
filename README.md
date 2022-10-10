# BC-Loss
Official code of "Incorporating Bias-aware Margins into Contrastive Loss for Collaborative Filtering" (2022 NeurIPS)

We provide implementation for various baselines presented in the paper. For data, the In-Distribution(test_id) and Out-of-Distribution(test_ood) test splits for Amazon-book, Tencent and Alibaba-Ifashion datasets are provided.

## Run the Code
To run the code, First run:
```python setup.py build_ext --inplace```
to install tools used in evaluation


### MF backbone
For models with MF as backbone, use models with random negative sampling strategy. For example:

MFBPR Training(equivalent to 0 layer LightGCN):

```python main.py --modeltype LGN --dataset tencent.new --n_layers 0 --neg_sample 1```

INFONCE Training:

```python main.py --modeltype INFONCE --dataset tencent.new  --n_layers 0 --neg_sample 128```

BC-LOSS Training:

```python main.py --modeltype BC_LOSS --dataset tencent.new --n_layers 0 --neg_sample 128```


### LightGCN backbone
For models with LightGCN as backbone, use models with in-batch negative sampling strategy. For example:

LightGCN Training:

```python main.py --modeltype LGN --dataset tencent.new --n_layers 2 --neg_sample 1```

INFONCE Training:

```python main.py --modeltype INFONCE_batch --dataset tencent.new  --n_layers 2 --neg_sample -1```

BC-LOSS Training:

```python main.py --modeltype BC_LOSS_batch --dataset tencent.new --n_layers 2 --neg_sample -1```

Details of hyperparameter settings for various baselines can be found in the paper.


## Requirements

python == 3.7.10

pytorch == 1.9.1+cu102


## Reference

@inproceedings{bc_loss,
      title     = {Incorporating Bias-aware Margins into Contrastive Loss for Collaborative Filtering},
      author    = {An Zhang and Wenchang Ma and Xiang Wang and Tat-seng Chua},
      booktitle = {{NeurIPS}},
      year      = {2022},
}










