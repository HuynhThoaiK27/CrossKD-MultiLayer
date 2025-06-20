# 🧠 CrossKD-IFC: Cross-Head Knowledge Distillation with Intermediate Feature Combination

This repository contains the implementation of our improved knowledge distillation method for object detection:  
**CrossKD-IFC** – an enhancement of CrossKD with intermediate feature aggregation.

---

## 📖 Overview

**Knowledge Distillation (KD)** has been proven to be an effective model compression technique for training compact object detectors. While most recent KD methods primarily focus on **feature imitation**, we propose an improved version of **CrossKD**—a general and effective **prediction mimicking-based KD approach**.

In our method, **intermediate features from multiple layers** of the student model's detection head are **combined and transferred** to the teacher model's detection head. The resulting **cross-head predictions** are then forced to mimic the teacher's outputs, helping to reduce conflicts between ground-truth labels and the teacher’s predictions. This enhances both the **effectiveness and training stability** of the distillation process.

### 🔬 Key Improvements
- 💡 Unlike the original CrossKD that uses only one intermediate feature layer, our method **aggregates features from multiple layers**.
- ⚙️ This **multi-layer feature fusion** provides richer, more informative representations for distillation.
- 🚀 We retain the **original loss functions** from CrossKD, making our method easy to plug into existing frameworks.

### 📊 Experimental Results

| Dataset     | Teacher (Backbone)      | Student (Backbone)     | Method           | mAP   |
|-------------|--------------------------|-------------------------|------------------|--------|
| Pascal VOC  | Faster R-CNN (ResNet-101) | Faster R-CNN (ResNet-50) | Baseline         | 70.1   |
|             |                          |                          | CrossKD-IFC      | **73.5** |
| COCO        | Faster R-CNN (ResNet-50)  | Faster R-CNN (ResNet-18) | Baseline         | 33.5   |
|             |                          |                          | CrossKD-IFC      | **35.9** |

These results confirm that our **Intermediate Feature Combination** strategy outperforms the original CrossKD and other KD methods.

---

##  Installation

Our code is based on **https://github.com/jbwang1997/CrossKD** Please follow the installation of CrossKD and make sure you can run it successfully.

## Add and Replace the codes
Replace the mmdet/models/detectors/crosskd_two_stage.py in CrossKD's codes with crosskd_two_state.py in our codes.

Add the crosskd_r18_faster-rcnn_r50_fpn_1x_coco.py in our codes to CrossKD's configs/crosskd/ .





