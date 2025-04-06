# Comparison of two architectures
# AlexNet-from-scratch

# Cats vs Dogs Classification: LeNet vs. AlexNet

This repository contains implementations and experiments comparing two architectures for classifying cats and dogs:

- **LeNet:** A classic, lightweight architecture originally designed for digit recognition.
- **AlexNet :** A deeper convolutional network with advanced preprocessing, inspired by architectures trained on ImageNet.

Both models were trained on the same Cats vs Dogs dataset for a fair comparison.

---

## Dataset

- **Dataset:** [Cats vs Dogs](https://www.microsoft.com/en-us/download/details.aspx?id=54765)
- **Structure:** Images are organized in subdirectories for each class (`/train/cats`, `/train/dogs`, `/test/cats`, `/test/dogs`).
- **Preprocessing:**
    - **LeNet:** Images resized to **64x64**, rescaled to [0, 1]. Minimal augmentation (random horizontal flip, rotation).
    - **AlexNet:** Images resized to **224x224**, rescaled to [0, 1] then normalized using ImageNet mean `[0.485, 0.456, 0.406]` and std `[0.229, 0.224, 0.225]`. Data augmentation (flip, rotation) applied.

---

## Architecture Comparison

| Feature | **LeNet** | **Modern CNN** |
| --- | --- | --- |
| **Input Size** | 64×64×3 | 224×224×3 |
| **Preprocessing** | Rescaling to [0, 1] | Rescaling to [0, 1] + ImageNet normalization |
| **Data Augmentation** | Random horizontal flip, rotation | Random horizontal flip, rotation |
| **Network Depth** | 2–3 convolutional layers + pooling | 5+ convolutional layers + pooling + BatchNorm/Dropout |
| **Parameter Count** | ~60K (lightweight) | ~1M+ (more capacity) |
| **Training Epochs** | 20 | 20 |
| **Optimizer** | Adam | Adam |
| **Validation Accuracy** | ~69% | ~89% |
| **Inference Speed** | Fast, low computational cost | Slower, higher computational cost |
| **Ideal Use Case** | Resource-constrained or educational | High-accuracy classification tasks |

---

## Training Details

### LeNet Model

- **Input:** 64×64 images
- **Normalization:** Pixel values scaled to [0,1]
- **Augmentation:** Optional random flip and rotation
- **Model Complexity:** Fewer layers and parameters, resulting in lower accuracy (~69%) but faster training.

### AlexNet Model

- **Input:** 224×224 images
- **Normalization:** Standard ImageNet normalization applied after rescaling
- **Augmentation:** Same as LeNet for consistency
- **Model Complexity:** Deeper architecture with additional convolutional layers, BatchNormalization, and Dropout. Achieves higher accuracy (~89%) but requires more computational resources.


### Results & Discussion
- **LeNet:** Offers a lightweight solution with faster training and inference, achieving ~67% validation accuracy. Suitable for learning and low-resource applications.

- **Alexnet:** With more capacity and advanced preprocessing, it significantly improves classification performance (~88% validation accuracy) but at the cost of higher computational demands.

- ### Conclusion
-**This comparative study demonstrates that while LeNet can be adapted to the Cats vs Dogs dataset, modern CNN architectures with appropriate preprocessing and regularization yield superior performance. The choice of architecture depends on the balance between available resources and the desired accuracy.**
