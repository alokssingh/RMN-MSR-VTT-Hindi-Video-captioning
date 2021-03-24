# RMN_MSR-VTT-Hindi-VC

# Learning to Discretely Compose Reasoning Module Networks for Video Captioning (IJCAI2020)
## Introduction
This code is the Pytorch implementation of RNM forked from [tgc1997](https://github.com/tgc1997/RMN) and the data Hindi MSR-VTT dataset is created by [alokssingh](https://github.com/alokssingh/MSR-VTT-captioning). Modification in the original code are made for the compatiablity with Hindi text. 
This implementation of [RNM](https://arxiv.org/abs/2007.09049) is used as a baseline model.

## Dependencies
* Python 3.7.3 (other versions may also work)
* Pytorch 1.4.0 (other versions may also work)
* pickle
* tqdm
* h5py
* matplotlib
* numpy
* tensorboard_logger
* CUDA 10.1


1. Download visual features from [MSR-VTT](https://rec.ustc.edu.cn/share/26685ac0-ba08-11ea-866f-6fc664dfaa3b) and text features from [MSR-VTT-Hindi-text](https://drive.google.com/drive/folders/1E4a5u2sge7JVkKnEu_28DHMsBVL8w6MO?usp=sharing) and put them in `data` folder.
2. Download evauation tool from [caption-eval](https://github.com/tgc1997/RMN)
3. POS tags for Hindi text are generated using [Stanford POS tagger](https://nlp.stanford.edu/software/tagger.shtml)
## Training command example:
```python
python train.py --dataset=msr-vtt --model=RMN --result_dir=results/msr-vtt_model --use_lin_loss \
 --learning_rate_decay --learning_rate_decay_every=5 --learning_rate_decay_rate=3 \
 --use_loc --use_rel --use_func --use_multi_gpu --learning_rate=1e-4 --attention=gumbel \
 --hidden_size=1300 --att_size=1024 --train_batch_size=32 --test_batch_size=8
```
## Evaluation command example:
```python
python evaluate.py --dataset=msr-vtt --model=RMN --result_dir=results/msr-vtt_model \
 --use_loc --use_rel --use_func --hidden_size=1300 --att_size=1024 \
 --test_batch_size=2 --beam_size=2 --eval_metric=CIDEr
```
## Acknowledgements
1. [Learning to Discretely Compose Reasoning Module Networks for Video Captioning](https://arxiv.org/abs/2007.09049)
2. [tgc1997](https://github.com/tgc1997/RMN)
3. [alokssingh](https://github.com/alokssingh/MSR-VTT-captioning)
