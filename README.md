# Pytorch-CycleGAN
Adpated from (https://github.com/aitorzip/PyTorch-CycleGAN)

## Prerequisites
Code is tested on python==3.7.2, visdom==0.1.8.9, torch==1.6.0+cu101. It hasn't been tested on other versions

### [PyTorch & torchvision](http://pytorch.org/)
Follow the instructions in [pytorch.org](http://pytorch.org) for your current setup

### [Visdom](https://github.com/facebookresearch/visdom)
To plot loss graphs and draw images in a nice web browser view
```
pip3 install visdom
```

## How to use
### fire up visdom server
```
python -m visdom.server
```
WARNING: fire up the visdom server before run the training code to view intermeidate results and avoid warning messages

After starting the visdom server, view intermediate result at http://localhost:8097 in real time

### training and testing
sample training and testing scripts are shown below. Argument options can be found in train.py (train_better.py) and test.py
```python
# naive CycleGAN
python train.py --dataroot datasets/ct2mri/ --cuda --size=110 --n_epochs=200 --decay_epoch=100 --batchSize=50 --saveDir naive_gan_ckpt

python test.py --dataroot datasets/rire/ --cuda --size=110 --generator_A2B output/naive_gan_ckpt/netG_A2B.pth --generator_B2A output/naive_gan_ckpt/netG_B2A.pth --saveDir naive_gan_rire

# modified CycleGAN
python train_better.py --dataroot datasets/ct2mri/ --cuda --n_epochs=300 --decay_epoch=150 --batchSize=64 --saveDir better_gan_ckpt

python test.py --dataroot datasets/rire/ --cuda --size=110 --generator_A2B output/better_gan_ckpt/netG_A2B.pth --generator_B2A output/better_gan_ckpt/netG_B2A.pth --saveDir better_gan_rire
```








