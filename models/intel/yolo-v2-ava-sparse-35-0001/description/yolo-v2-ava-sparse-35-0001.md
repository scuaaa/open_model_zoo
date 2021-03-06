# yolo-v2-ava-sparse-35-0001

## Use Case and High-Level Description

This is a re-implemented and re-trained version of [YOLO v2](https://arxiv.org/abs/1612.08242) object detection network trained with VOC2012 training dataset.
[Network weight pruning](https://arxiv.org/abs/1710.01878) is applied to sparsify convolution layers (35% of network parameters are set to zeros).

## Example

## Specification

| Metric                       | Value        |
|------------------------------|--------------|
| Mean Average Precision (mAP) | 63.71%       |
| Flops                        | 48.29Bn*     |
| Source framework             | Tensorflow** |

Average Precision metric described in: Mark Everingham et al.
["The PASCAL Visual Object Classes (VOC) Challenge"](http://host.robots.ox.ac.uk/pascal/VOC/pubs/everingham10.pdf).
Tested on VOC 2012 validation dataset.

## Performance

## Inputs

1. name: "input" , shape: [1x3x416x416] - An input image in the format [BxCxHxW],
  where:
    - B - batch size
    - C - number of channels
    - H - image height
    - W - image width.
  Expected color order is BGR.

## Outputs

1. The net outputs a blob with the shape: [1, 21125], which can be reshaped to [5, 25, 13, 13],
   where each number corresponds to [`num_anchors`, `cls_reg_obj_params`, `y_loc`, `x_loc`], respectively.
    - `num_anchors`: number of anchor boxes, each spatial location specified by `y_loc` and `x_loc` has 5 anchors.
    - `cls_reg_obj_params`: parameters for classification and regression. The values are made up of the followings:
      * Regression parameters (4)
      * Objectness score (1)
      * Class score (20)
    - `y_loc` and `x_loc`: spatial location of each grid.

## Legal Information
[*] Same as the original implementation.

[**] Other names and brands may be claimed as the property of others.
