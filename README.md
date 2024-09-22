## **Deep Learning for Image Classification and Object Detection**

This project showcases deep learning experiments for Image Classification and Object Detection tasks.

### **Introduction**

#### **Image Classification**
- **Architecture**: ResNet50, a deep CNN known for its residual learning, solves the vanishing gradient problem in deep networks.
- **Baseline Model**: Trained with ImageNet weights on 20 classes (birds and dogs), with end-to-end training.
- **Customization**: Fine-tuned by removing some convolutional layers and using regularization techniques for better dataset alignment. The model was initialized with ImageNet weights, trained without freezing any layers.

#### **Object Detection**
- **Faster R-CNN**: Two-stage detection with a Region Proposal Network (RPN) for object localization, followed by classification and bounding box refinement.
- **YOLOv5**: Single-shot detection model known for real-time performance, directly predicting bounding boxes and class probabilities. Used for detecting solar panel damage in thermal images.

### **Datasets**
1. **Image Classification**: 20 classes of birds and dogs, split 70:15:15 for training, validation, and testing.
2. **Object Detection**: Thermal images of solar panel damage (5 classes), split 70:15:15 with 1167 training, 250 validation, and 250 testing images.

### CNN Architecture for Image Classification

#### Baseline Architecture
- **Model**: ResNet50 with 5 stages, initialized with ImageNet weights.
- **Head**: Global Average Pooling, dense layer (1024 units), softmax for 20-class classification.
- **Compilation**: Adam (1e-4), Categorical Cross-Entropy, Accuracy metric.

#### Customized Architecture
- **Changes**: Removed Stage 5, kept layers up to Stage 4, Block 2-2.
- **Head**: Dense layer with L2 (0.45), dropout (0.65), and softmax for classification.

#### Enhancements
- **Data Augmentation**: Rotation (20°), zoom (20%), horizontal flip.
- **Simplification**: Reduced complexity to prevent overfitting.
- **Regularization**: L2 and dropout for improved generalization.

### CNN Architecture for Object Detection

#### 1. Faster R-CNN
- **Backbone**: ResNet50 with residual blocks for multi-scale feature extraction.
- **Region Proposal Network (RPN)**: Generates object proposals by sliding a small window across the feature map.
- **RoI Pooling**: Extracts fixed-size feature maps for each proposal.
- **RoI Head**: Performs classification and bounding box regression.
- **Output**: Bounding box coordinates and class probabilities.

#### 2. YOLOv5
- **Backbone**: YOLOv5 small with convolutional layers, including SPP for feature extraction at different scales.
- **Head**: Processes features and predicts bounding boxes and class probabilities using anchor boxes.

### Conclusion

Efforts to enhance the customized ResNet50 model using techniques like data augmentation, L2 regularization, and dropout did not outperform the baseline model. The baseline achieved perfect training accuracy and better generalization with lower validation loss and strong test performance, highlighting the importance of careful model design. 

In object detection, Faster R-CNN's complexity results in longer training times due to its multi-stage architecture. However, YOLOv5 demonstrates faster training and superior precision and recall for underrepresented classes, maintaining more stable performance across all object classes. This makes YOLOv5 a more efficient and reliable choice for real-time object detection tasks.
