# BoxMOT: pluggable SOTA tracking modules for segmentation, object detection and pose estimation models

<div align="center">
  <p>
  <img src="assets/images/track_all_seg_1280_025conf.gif" width="400"/>
  </p>
  <br>
  <div>
  <a href="https://github.com/mikel-brostrom/yolov8_tracking/actions/workflows/ci.yml"><img src="https://github.com/mikel-brostrom/yolov8_tracking/actions/workflows/ci.yml/badge.svg" alt="CI CPU testing"></a>
  <a href="https://pepy.tech/project/boxmot"><img src="https://static.pepy.tech/badge/boxmot"></a>
  <br>
  <a href="https://colab.research.google.com/drive/18nIqkBr68TkK8dHdarxTco6svHUJGggY?usp=sharing"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a>
<a href="https://doi.org/10.5281/zenodo.8132989"><img src="https://zenodo.org/badge/DOI/10.5281/zenodo.8132989.svg" alt="DOI"></a>

  </div>
</div>

## Introduction

This repo contains a collections of pluggable state-of-the-art multi-object trackers for segmentation, object detection and pose estimation models. For the methods using appearance description, both heavy ([CLIPReID](https://arxiv.org/pdf/2211.13977.pdf)) and lightweight state-of-the-art ReID models ([LightMBN](https://arxiv.org/pdf/2101.10774.pdf), [OSNet](https://arxiv.org/pdf/1905.00953.pdf) and more) are available for automatic download. I have tested these models on one video people.mp4 to show how to use this package together with popular object detection models such as: [Yolov8](https://github.com/ultralytics), [Yolo-NAS](https://github.com/Deci-AI/super-gradients) and [YOLOX](https://github.com/Megvii-BaseDetection/YOLOX). Furthermore, i downloaded MOT17 dataset for benchmarking tracking results.

<div align="center">

|  Tracker | HOTA↑ | MOTA↑ | IDF1↑ |
| -------- | ----- | ----- | ----- |
| [BoTSORT](https://arxiv.org/pdf/2206.14651.pdf)    | 77.8 | 78.9 | 88.9 |
| [DeepOCSORT](https://arxiv.org/pdf/2302.11813.pdf) | 77.4 | 78.4 | 89.0 |
| [OCSORT](https://arxiv.org/pdf/2203.14360.pdf)     | 77.4 | 78.4 | 89.0 |
| [HybridSORT](https://arxiv.org/pdf/2308.00783.pdf) | 77.3 | 77.9 | 88.8 |
| [ByteTrack](https://arxiv.org/pdf/2110.06864.pdf)  | 75.6 | 74.6 | 86.0 |
| [StrongSORT](https://arxiv.org/pdf/2202.13514.pdf) |      | | |
| <img width=200/>                                   | <img width=100/> | <img width=100/> | <img width=100/> |

<sub> NOTES: performed on the 10 first frames of each MOT17 sequence. The detector used is ByteTrack's YoloXm, trained on: CrowdHuman, MOT17, Cityperson and ETHZ. Each tracker is configured with its original parameters found in their respective official repository.</sub>

</div>

</details>

<details>
<summary>Tutorials</summary>

* [Yolov8 training (link to external repository)](https://docs.ultralytics.com/modes/train/)&nbsp;
* [Deep appearance descriptor training (link to external repository)](https://kaiyangzhou.github.io/deep-person-reid/user_guide.html)&nbsp;
* [ReID model export to ONNX, OpenVINO, TensorRT and TorchScript](https://github.com/mikel-brostrom/yolo_tracking/wiki/ReID-multi-framework-model-export)&nbsp;
* [Evaluation on custom tracking dataset](https://github.com/mikel-brostrom/yolo_tracking/wiki/How-to-evaluate-on-custom-tracking-dataset)&nbsp;
* [ReID inference acceleration with Nebullvm](https://colab.research.google.com/drive/1APUZ1ijCiQFBR9xD0gUvFUOC8yOJIvHm?usp=sharing)&nbsp;

  </details>

<details>
<summary>Experiments</summary>

In inverse chronological order:

* [Evaluation of the params evolved for first half of MOT17 on the complete MOT17](https://github.com/mikel-brostrom/Yolov5_StrongSORT_OSNet/wiki/Evaluation-of-the-params-evolved-for-first-half-of-MOT17-on-the-complete-MOT17)

* [Segmentation model vs object detetion model on MOT metrics](https://github.com/mikel-brostrom/Yolov5_StrongSORT_OSNet/wiki/Segmentation-model-vs-object-detetion-model-on-MOT-metrics)

* [Effect of masking objects before feature extraction](https://github.com/mikel-brostrom/Yolov5_StrongSORT_OSNet/wiki/Masked-detection-crops-vs-regular-detection-crops-for-ReID-feature-extraction)

* [conf-thres vs HOTA, MOTA and IDF1](https://github.com/mikel-brostrom/Yolov5_StrongSORT_OSNet/wiki/conf-thres-vs-MOT-metrics)

* [Effect of KF updates ahead for tracks with no associations on MOT17](https://github.com/mikel-brostrom/Yolov5_StrongSORT_OSNet/wiki/Effect-of-KF-updates-ahead-for-tracks-with-no-associations,-on-MOT17)

* [Effect of full images vs 1280 input to StrongSORT on MOT17](https://github.com/mikel-brostrom/Yolov5_StrongSORT_OSNet/wiki/Effect-of-passing-full-image-input-vs-1280-re-scaled-to-StrongSORT-on-MOT17)

* [Effect of different OSNet architectures on MOT16](https://github.com/mikel-brostrom/Yolov5_StrongSORT_OSNet/wiki/OSNet-architecture-performances-on-MOT16)

* [Yolov5 StrongSORT vs BoTSORT vs OCSORT](https://github.com/mikel-brostrom/Yolov5_StrongSORT_OSNet/wiki/StrongSORT-vs-BoTSORT-vs-OCSORT)
    * Yolov5 [BoTSORT](https://arxiv.org/abs/2206.14651) branch: https://github.com/mikel-brostrom/Yolov5_StrongSORT_OSNet/tree/botsort

* [Yolov5 StrongSORT OSNet vs other trackers MOT17](https://github.com/mikel-brostrom/Yolov5_StrongSORT_OSNet/wiki/MOT-17-evaluation-(private-detector))&nbsp;

* [StrongSORT MOT16 ablation study](https://github.com/mikel-brostrom/Yolov5_StrongSORT_OSNet/wiki/Yolov5DeepSORTwithOSNet-vs-Yolov5StrongSORTwithOSNet-ablation-study-on-MOT16)&nbsp;

* [Yolov5 StrongSORT OSNet vs other trackers MOT16 (deprecated)](https://github.com/mikel-brostrom/Yolov5_StrongSORT_OSNet/wiki/MOT-16-evaluation)&nbsp;

  </details>

#### News

* HybridSORT available (August 2023)
* SOTA CLIP-ReID people and vehicle models available (August 2023)


## Why BOXMOT?

Today's multi-object tracking options are heavily dependant on the computation capabilities of the underlaying hardware. BOXMOT provides a great variety of setup options that meet different hardware limitations: CPU only, low memory GPUs... Everything is designed with simplicity and flexibility in mind. If  tracking results ARE NOT GOOD on custom dataset with the out-of-the-box tracker configurations, use the `examples/evolve.py` script for tracker hyperparameter tuning.

## Installation

Start with [**Python>=3.8**](https://www.python.org/) environment.

If you want to run the YOLOv8, YOLO-NAS or YOLOX examples:

```
git clone https://github.com/mikel-brostrom/yolo_tracking.git
cd yolo_tracking
pip install -v -e .
```

but if you only want to import the tracking modules you can simply:

```
pip install boxmot
```

## YOLOv8 | YOLO-NAS | YOLOX examples

<details>
<summary>Tracking</summary>

<details>
<summary>Yolo models</summary>
# Tracking

```
usage: track.py [-h] [--yolo-model YOLO_MODEL] [--reid-model REID_MODEL] [--tracking-method TRACKING_METHOD] [--source SOURCE]
                [--imgsz IMGSZ [IMGSZ ...]] [--conf CONF] [--iou IOU] [--device DEVICE] [--show] [--save]
                [--classes CLASSES [CLASSES ...]] [--project PROJECT] [--name NAME] [--exist-ok] [--half] [--vid-stride VID_STRIDE]
                [--show-labels] [--show-conf] [--save-txt] [--save-id-crops] [--save-mot] [--line-width LINE_WIDTH] [--per-class]
                [--verbose] [--vid_stride VID_STRIDE]
```
For the time being, we can use above command in this manner:

```bash
$ python track.py --yolo-model yolov8n   --source people.mp4    # bboxes only
  python track.py --yolo-model yolo_nas_s    --source people.mp4  # bboxes only
  python track.py --yolo-model yolox_n      --source people.mp4 # bboxes only
                                        yolov8n-seg  --source people.mp4  # bboxes + segmentation masks
                                        yolov8n-pose  --source path/to/your/video/file.mp4 # bboxes + pose estimation

```
Results : 
with different detectors , for object detection as well as segmentation models following results of tracking are achieved

|  Detector | Speed | inference | postprocess |tracking per image at shape (1, 3, 384, 640)
| -------- | ----- | ----- | ----- |-------|
| yolov8n  | 1.1ms | 6.1ms | 0.9ms |46.1ms|
| yolo_nas_s| 1.4ms | 47.8ms| 0.2ms |32.7ms|
| yolox_n | 1.8ms | 10.5ms | 10.5ms |127.8ms|
| yolov8n-seg| 1.0ms | 7.0ms|1.3ms |44.6ms |
| yolov8n-pose | 1.0ms | 6.8ms | 0.9ms|22.9ms|
| <img width=200/> | <img width=100/> | <img width=100/> | <img width=100/> |<img width=100/>|


  </details>

<details>
<summary>Tracking methods</summary>

```bash
$ python track.py --tracking-method deepocsort --source people.mp4 
                                             strongsort
                                             ocsort
                                             bytetrack
                                             botsort
```

Results : 
with different trackers ,  following results of tracking are achieved

|  Tracker| Speed | inference | postprocess |tracking per image at shape (1, 3, 384, 640)
| -------- | ----- | ----- | ----- |-------|
| deepocsort |1.0ms |5.9ms | 0.8ms |45.8ms |
| strongsort| 1.3ms | 12.4ms| 1.5ms |123.4ms|
| ocsort| 1.0ms | 5.8ms | 0.8ms|4.5ms|
| bytetrack| 1.0ms | 5.7ms|0.8ms |5.2ms |
| botsort | 1.0ms | 5.9ms |0.8ms|44.3ms|
| <img width=200/> | <img width=100/> | <img width=100/> | <img width=100/> |<img width=100/>|


</details>

<details>
<summary>Tracking sources</summary>

Tracking can be run on most video formats

```bash
$ python examples/track.py --source 0                               # webcam
                                    img.jpg                         # image
                                    vid.mp4                         # video
                                    path/                           # directory
                                    path/*.jpg                      # glob
                                    'https://youtu.be/Zgi9g1ksQHc'  # YouTube
                                    'rtsp://example.com/media.mp4'  # RTSP, RTMP, HTTP stream
```

</details>

<details>
<summary>Select ReID model</summary>

Some tracking methods combine appearance description and motion in the process of tracking. For those which use appearance, you can choose a ReID model based on your needs from this [ReID model zoo](https://kaiyangzhou.github.io/deep-person-reid/MODEL_ZOO). These model can be further optimized for you needs by the [reid_export.py](https://github.com/mikel-brostrom/yolo_tracking/blob/master/boxmot/deep/reid_export.py) script

```bash
$ python examples/track.py --source 0 --reid-model lmbn_n_cuhk03_d.pt               # lightweight
                                                   osnet_x0_25_market1501.pt
                                                   mobilenetv2_x1_4_msmt17.engine
                                                   resnet50_msmt17.onnx
                                                   osnet_x1_0_msmt17.pt
                                                   clip_market1501.pt               # heavy
                                                   clip_vehicleid.pt
                                                   ...
```

</details>

<details>
<summary>Filter tracked classes</summary>

By default the tracker tracks all MS COCO classes.

If you want to track a subset of the classes that you model predicts, add their corresponding index after the classes flag,

```bash
python track.py --source anyvideoofyourchoice.mp4 --yolo-model yolov8s.pt --classes 16 17  # COCO yolov8 model. Track cats and dogs, only
python track.py --source people.mp4 --yolo-model yolov8s.pt --classes 16 17  # COCO yolov8 model. Track people only
```

# Results : Speed: 1.0ms preprocess, 6.2ms inference, 0.9ms postprocess, 42.8ms tracking per image at shape (1, 3, 384, 640)

[Here](https://tech.amikelive.com/node-718/what-object-categories-labels-are-in-coco-dataset/) is a list of all the possible objects that a Yolov8 model trained on MS COCO can detect. Notice that the indexing for the classes in this repo starts at zero

</details>

<details>
<summary>MOT compliant results</summary>

Can be saved to your experiment folder `runs/track/exp*/` by

```
python track.py --source people.mp4 --yolo-model yolov8s.pt --save-mot
python track.py --source people.mp4 --yolo-model yolov8s.pt --save-mot --show  --save 
```
# Results for command 1 : Speed: 1.0ms preprocess, 6.2ms inference, 0.8ms postprocess, 43.1ms tracking per image at shape (1, 3, 384, 640)
MOT results saved to /home/caic/Downloads/yolo_tracking-master/runs/track/exp/mot/people.mp4.txt
# Results for command 2 : Speed: 1.0ms preprocess, 6.2ms inference, 0.8ms postprocess, 43.4ms tracking per image at shape (1, 3, 384, 640)
Results saved to /home/caic/Downloads/yolo_tracking-master/runs/track/exp2
MOT results saved to /home/caic/Downloads/yolo_tracking-master/runs/track/exp2/mot/people.mp4.txt


</details>

</details>

<details>
<summary>Evaluation</summary>

Evaluate a combination of detector, tracking method and ReID model on standard MOT dataset or you custom one by. Person re-identification (ReID) is an intelligent video surveillance technology that retrieves the same person from different cameras. This task is extremely challenging due to changes in person poses, different camera views, and occlusion

```bash
$ python3 examples/val.py --yolo-model yolo_nas_s.pt --reid-model osnetx1_0_dukemtcereid.pt --tracking-method deepocsort --benchmark MOT16
                          --yolo-model yolox_n.pt    --reid-model osnet_ain_x1_0_msmt17.pt  --tracking-method ocsort     --benchmark MOT17
                          --yolo-model yolov8s.pt    --reid-model lmbn_n_market.pt          --tracking-method strongsort --benchmark <your-custom-dataset>
```

</details>

<details>
<summary>Evolution</summary>

We use a fast and elitist multiobjective genetic algorithm for tracker hyperparameter tuning. By default the objectives are: HOTA, MOTA, IDF1. Run it by

```bash
$ python examples/evolve.py --tracking-method strongsort --benchmark MOT17 --n-trials 100  # tune strongsort for MOT17
                            --tracking-method ocsort     --benchmark <your-custom-dataset> --objective HOTA # tune ocsort for maximizing HOTA on your custom tracking dataset
```

The set of hyperparameters leading to the best HOTA result are written to the tracker's config file.

</details>


## Custom object detection model tracking example

<details>
<summary>Minimalistic</summary>

```python
import cv2
import numpy as np
from pathlib import Path

from boxmot import DeepOCSORT


tracker = DeepOCSORT(
    model_weights=Path('osnet_x0_25_msmt17.pt'), # which ReID model to use
    device='cuda:0',
    fp16=False,
)

vid = cv2.VideoCapture(0)

while True:
    ret, im = vid.read()

    # substitute by your object detector, output has to be N X (x, y, x, y, conf, cls)
    dets = np.array([[144, 212, 578, 480, 0.82, 0],
                    [425, 281, 576, 472, 0.56, 65]])

    tracks = tracker.update(dets, im) # --> (x, y, x, y, id, conf, cls, ind)
```

</details>


<details>
<summary>Complete</summary>

```python
import cv2
import numpy as np
from pathlib import Path

from boxmot import DeepOCSORT


tracker = DeepOCSORT(
    model_weights=Path('osnet_x0_25_msmt17.pt'), # which ReID model to use
    device='cuda:0',
    fp16=True,
)

vid = cv2.VideoCapture(0)
color = (0, 0, 255)  # BGR
thickness = 2
fontscale = 0.5

while True:
    ret, im = vid.read()

    # substitute by your object detector, input to tracker has to be N X (x, y, x, y, conf, cls)
    dets = np.array([[144, 212, 578, 480, 0.82, 0],
                    [425, 281, 576, 472, 0.56, 65]])

    tracks = tracker.update(dets, im) # --> (x, y, x, y, id, conf, cls, ind)

    xyxys = tracks[:, 0:4].astype('int') # float64 to int
    ids = tracks[:, 4].astype('int') # float64 to int
    confs = tracks[:, 5]
    clss = tracks[:, 6].astype('int') # float64 to int
    inds = tracks[:, 7].astype('int') # float64 to int

    # in case you have segmentations or poses alongside with your detections you can use
    # the ind variable in order to identify which track is associated to each seg or pose by:
    # segs = segs[inds]
    # poses = poses[inds]
    # you can then zip them together: zip(tracks, poses)

    # print bboxes with their associated id, cls and conf
    if tracks.shape[0] != 0:
        for xyxy, id, conf, cls in zip(xyxys, ids, confs, clss):
            im = cv2.rectangle(
                im,
                (xyxy[0], xyxy[1]),
                (xyxy[2], xyxy[3]),
                color,
                thickness
            )
            cv2.putText(
                im,
                f'id: {id}, conf: {conf}, c: {cls}',
                (xyxy[0], xyxy[1]-10),
                cv2.FONT_HERSHEY_SIMPLEX,
                fontscale,
                color,
                thickness
            )

    # show image with bboxes, ids, classes and confidences
    cv2.imshow('frame', im)

    # break on pressing q
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

vid.release()
cv2.destroyAllWindows()
```

</details>

<details>
<summary>Tiled inference</summary>
  
```py
from sahi import AutoDetectionModel
from sahi.predict import get_sliced_prediction
import cv2
import numpy as np
from pathlib import Path
from boxmot import DeepOCSORT


tracker = DeepOCSORT(
    model_weights=Path('osnet_x0_25_msmt17.pt'), # which ReID model to use
    device='cpu',
    fp16=False,
)

detection_model = AutoDetectionModel.from_pretrained(
    model_type='yolov8',
    model_path='yolov8n.pt',
    confidence_threshold=0.5,
    device="cpu",  # or 'cuda:0'
)

vid = cv2.VideoCapture(0)
color = (0, 0, 255)  # BGR
thickness = 2
fontscale = 0.5

while True:
    ret, im = vid.read()

    # get sliced predictions
    result = get_sliced_prediction(
        im,
        detection_model,
        slice_height=256,
        slice_width=256,
        overlap_height_ratio=0.2,
        overlap_width_ratio=0.2
    )
    num_predictions = len(result.object_prediction_list)
    dets = np.zeros([num_predictions, 6], dtype=np.float32)
    for ind, object_prediction in enumerate(result.object_prediction_list):
        dets[ind, :4] = np.array(object_prediction.bbox.to_xyxy(), dtype=np.float32)
        dets[ind, 4] = object_prediction.score.value
        dets[ind, 5] = object_prediction.category.id

    tracks = tracker.update(dets, im) # --> (x, y, x, y, id, conf, cls, ind)

    if tracks.shape[0] != 0:

        xyxys = tracks[:, 0:4].astype('int') # float64 to int
        ids = tracks[:, 4].astype('int') # float64 to int
        confs = tracks[:, 5].round(decimals=2)
        clss = tracks[:, 6].astype('int') # float64 to int
        inds = tracks[:, 7].astype('int') # float64 to int

        # print bboxes with their associated id, cls and conf
        for xyxy, id, conf, cls in zip(xyxys, ids, confs, clss):
            im = cv2.rectangle(
                im,
                (xyxy[0], xyxy[1]),
                (xyxy[2], xyxy[3]),
                color,
                thickness
            )
            cv2.putText(
                im,
                f'id: {id}, conf: {conf}, c: {cls}',
                (xyxy[0], xyxy[1]-10),
                cv2.FONT_HERSHEY_SIMPLEX,
                fontscale,
                color,
                thickness
            )

    # show image with bboxes, ids, classes and confidences
    cv2.imshow('frame', im)

    # break on pressing q
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

vid.release()
cv2.destroyAllWindows()
```

</details>

## Contributors

<a href="https://github.com/mikel-brostrom/yolo_tracking/graphs/contributors ">
  <img src="https://contrib.rocks/image?repo=mikel-brostrom/yolo_tracking" />
</a>

## Contact

For Yolo tracking bugs and feature requests please visit [GitHub Issues](https://github.com/mikel-brostrom/yolo_tracking/issues).
For business inquiries or professional support requests please send an email to: yolov5.deepsort.pytorch@gmail.com
