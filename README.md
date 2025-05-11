# soil-classification-nea-deep-learning
 
## CNNs applied to satellite imagery from NEA Argentina

A deep learning project for land use classification using satellite images and CNNs, focused on generalization to the NEA region (Argentina).  

---

## Objectives

- Develop a model to detect forest areas from Sentinel satellite images.
- Train CNNs using the **EuroSat** dataset.
- Evaluate the model’s performance with real satellite images from the **Argentinian NEA** (Northeast).

---

## Dataset

### EuroSat (Training and Validation)
- 27,000 multi-class satellite images (64×64 px, 10 classes).

### NEA Satellite Images (External Test)
- Sentinel-2 images from Misiones, Corrientes, and other NEA areas.
- Transformed into patches comparable to EuroSat (~800×800 m).
- Manually classified and used as external test data.

---

## Models Used

### Base Model: **ResNet-34**
- Data augmentation: rotations, flips, brightness, contrast.
- Training with **5-fold Cross Validation**.
- Optimizer: SGD + ReduceLROnPlateau.
- Accuracy on EuroSat: **~97.8%** (val) / **97.8%** (test).

### Custom Model: **Own CNN**
- Architecture with residual blocks and deep convolutional layers.
- Accuracy on EuroSat test: **90.92%**
- Accuracy on NEA test: **24.31%**

---

## Main Results

- **EuroSat**: Both models achieved high accuracy (>90%) on in-domain test data.
- **NEA**: Strong performance drop, especially in vegetation and water classes.
  - ResNet-34 Accuracy on NEA: **56%**
  - F1-score = 0 in some NEA classes (*HerbaceousVegetation, River, SeaLake*).
  - The model shows **dependency on the original EuroSat domain**.

---

## Conclusions

- CNNs perform well on known domains with consistent data.
- **Geographic generalization** remains a major challenge.
- Improving performance in Latin American contexts requires **diverse and representative training datasets**.
- This highlights the need for **locally sourced satellite imagery** in future research.
