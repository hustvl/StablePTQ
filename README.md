## StablePTQ

Stabilized Activation Scale Estimation for Precise Post-Training Quantization

## Usage
### 1. Download pre-trained FP model.
The pre-trained FP models in our experiment comes from [BRECQ](https://github.com/yhhhli/BRECQ), they can be downloaded in [link](https://github.com/yhhhli/BRECQ/releases/tag/v1.0).

### 2. Run experiments
Go into the exp/w2a4 directory. You can find config.yaml and run.sh for each arch. Execute the run.sh for quantized model. Other bit settings only need to change the corresponding bit number in yaml file.

## Results

It is important to note that we do not set the first and last layer in 8-bit like QDrop and BRECQ. 
Only the input of the first layer is fixed in 8-bit, that is to say, only the input of the whole network is 8-bit.

Results on low-bit activation in terms of accuracy on ImageNet.
| Methods |  Bits (W/A) | Res18 | Res50 | MNV2 | Reg600M | Reg3.2G | MNasx2 |
| ------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
|   Full Prec. |   32/32 |  71.00 | 76.63 | 72.63 | 73.52 | 78.46 | 76.53 |
|StablePTQ| 4/4 | 69.08 | 74.96 | 68.01 | 70.58 | 76.45 | 72.57 |
|StablePTQ| 2/4 | 62.45 | 66.41 | 51.70 | 59.40 | 63.75| 62.25|
|StablePTQ| 3/3 | 65.26 | 70.85 | 53.52 | 63.80 | 71.50 | 63.08 |
|StablePTQ| 2/2 | 48.66 | 48.36 | 9.78 | 32.56 | 44.58 | 22.53 |


## Reference
```
@article{hao2023stabilized,
  title={Stabilized activation scale estimation for precise Post-Training Quantization},
  author={Hao, Zhenyang and Wang, Xinggang and Liu, Jiawei and Yuan, Zhihang and Yang, Dawei and Liu, Wenyu},
  journal={Neurocomputing},
  pages={127120},
  year={2023},
  publisher={Elsevier}
}
```

## Thanks
Our code is based on [QDROP](https://github.com/wimh966/QDrop/tree/qdrop) by @wimh966.
