# Combine RGB painting and PointPillars
**Creator: Thuy C. Nguyen; Date: July 23 2020**

-----
## Added features

* Augment input feature from `[x, y, z, r, cx, cy, cz, vx, vy]` to `[x, y, z, r, cx, cy, cz, vx, vy, R, G, B]` (9 to 12).
* Augmented objects, which are sampled from the database during the training, are also painted with RGB.
* RGB is normalized with mean and std as conventional in ImageNet.


-----
## Experiments

|     Model    | Autoscale LR | Total BS |  AP  |                                                           Config                                                          |
|:------------:|:------------:|:--------:|:----:|:-------------------------------------------------------------------------------------------------------------------------:|
| PointPillars |              |          | 77.1 |                                                          Baseline                                                         |
| PointPillars |       x      |    12    | 76.2 | [RGB painting; zero padding to GT-Aug](configs/subset/rgb_paint/hv_pointpillars_secfpn_6x2_80e_kitti-3d-car-rgb_paint.py) |
| PointPillars |       x      |    12    | 76.5 |        [Zero RGB painting](configs/subset/rgb_paint/hv_pointpillars_secfpn_6x2_80e_kitti-3d-car-rgb_paint_zero.py)        |
| PointPillars |       x      |    12    | 76.2 | [RGB painting; GT-Aug is also painted](configs/subset/rgb_paint/hv_pointpillars_secfpn_6x2_80e_kitti-3d-car-rgb_paint.py) |

**Conclusion**: RGB painting does not help the network.
