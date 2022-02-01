---
id: ifmGOHRpG2boYwe9mTk8d
title: Lec 4
desc: ''
updated: 1643520881078
created: 1643096100305
---
# Edge Detection

- identifying discontinuity in an image
- to get better idea about the shape and semantics
- provides more information than pixel level

## Edge Formation

- rapid change in intensity
- can be caused by:
  - ![](/assets/images/2022-01-30-10-37-43.png)
  - intensity or color change
  - surface normal discontinuity
  - depth discontinuity
  - surface color discontinuity
  - illumination discontinuity

## Edge Types

![](/assets/images/2022-01-30-10-45-04.png)
- **_due to sampling and quantization, real edges are noisy_**

## Edge Detector and Performance

- We need edge operator to produce:
  - Edge position
    - sub pixel level accuracy
  - Edge magnitude – Strength
  - Edge Orientation – Direction
- Performance measurement
  - High detection rate
  - Good localization
  - Low noise sensitivity