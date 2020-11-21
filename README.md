# Sparse R-CNN
Sparse R-CNN is a purely sparse, end-to-end method for object detection.
![](readme/fig.jpeg)

## Models
Method | inf_time | train_time | box AP | download
--- |:---:|:---:|:---:||:---
[R50_100pro_1x](projects/SparseR-CNN/configs/sparsercnn.res50.100pro.1x.yaml) | 23 FPS | 6.5h | 38.7 | [model](https://drive.google.com/drive/folders/)
[R50_100pro_3x](projects/SparseR-CNN/configs/sparsercnn.res50.100pro.3x.yaml) | 23 FPS | 19h  | 42.3 | [model](https://drive.google.com/drive/folders/)
[R50_300pro_3x](projects/SparseR-CNN/configs/sparsercnn.res50.300pro.3x.yaml) | 22 FPS | 24h  | 44.5 | [model](https://drive.google.com/drive/folders/)

Training time is on 8 GPUs with batchsize 16. Inference time is on single GPU. All GPUs are NVIDIA V100. 

## Installation
The codebases are built on top of [Detectron2](https://github.com/facebookresearch/detectron2) and [DETR](https://github.com/facebookresearch/detr).

#### Requirements
- Linux or macOS with Python ≥ 3.6
- PyTorch ≥ 1.5 and [torchvision](https://github.com/pytorch/vision/) that matches the PyTorch installation.
  You can install them together at [pytorch.org](https://pytorch.org) to make sure of this
- OpenCV is optional and needed by demo and visualization

#### Steps
1. Install and build libs
```
git clone https://github.com/PeizeSun/SparseR-CNN.git
cd SparseR-CNN
python setup.py build develop
```

2. Link coco dataset path to SparseR-CNN/datasets/coco

3. Train SparseR-CNN
```
python projects/SparseR-CNN/train_net.py --num-gpus 8 --config-file projects/SparseR-CNN/configs/sparsercnn.res50.100pro.1x.yaml
```

4. Evaluate SparseR-CNN
```
python projects/SparseR-CNN/train_net.py --num-gpus 8 --config-file projects/SparseR-CNN/configs/sparsercnn.res50.100pro.1x.yaml --eval-only MODEL.WEIGHTS path/to/model.pth
```

## License

SparseR-CNN is released under MIT License.


## Citing

If you use SparseR-CNN in your research or wish to refer to the baseline results published here, please use the following BibTeX entries:

```BibTeX

@article{peize2020sparse,
  title   =  {{SparseR-CNN}: End-to-End Object Detection with Learnable Proposal},
  author  =  {},
  journal =  {arXiv preprint arXiv:},
  year    =  {2020}
}

```
