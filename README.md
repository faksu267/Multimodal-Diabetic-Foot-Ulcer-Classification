# Multimodal-Diabetic-Foot-Ulcer-Classification
A multimodal deep learning framework for classifying Diabetic Foot Ulcer (DFU) stages using fused 4-channel RGB and thermal images.


Description
This repository contains the code and methodology for a multimodal deep learning approach designed to classify Diabetic Foot Ulcer (DFU) stages (Wagner Grades 0 to 5)

Diabetic foot ulcers require continuous monitoring to prevent severe complications such as amputation. To address this, we developed a system that leverages both RGB and Thermal imaging. While RGB images capture textural and morphological changes, thermal images detect hidden heat anomalies caused by inflammation or infection. By combining these two modalities into a single 4-channel tensor, our AI model significantly outperforms single-modality approaches

The framework uses transfer learning with several pre-trained CNN backbones (VGG16, ResNet50, InceptionV3, DenseNet121, EfficientNetV2) and a custom classification head
Evaluated using 5-fold stratified cross-validation, the VGG16-based multimodal (RGB+Thermal) model achieved a peak overall accuracy of 93.25% and a Matthews Correlation Coefficient (MCC) of 91.03%. Additionally, this project outlines a custom Raspberry Pi-based portable image acquisition system (utilizing a Pi Camera V2 and a Flir Lepton 3.5 thermal module), offering a practical infrastructure for in-home telehealth and remote DFU monitoring


Key Features
-Multimodal Data Fusion: Combines standard color (RGB) and heat-sensing (Thermal) data into a rich 4-channel input
-High Accuracy: Achieved 93.25% overall classification accuracy using a customized VGG16 architecture
  • Robust Evaluation: Implemented 5-fold stratified cross-validation and class-weighted loss functions to handle dataset imbalance effectively
  • Hardware Integration: Includes the architectural setup for a low-cost, 3D-printed Raspberry Pi smart monitoring device
  • Explainable AI (XAI): Utilizes Grad-CAM to visualize the model's focus, proving that the RGB+Thermal fusion correctly targets ulcer sites and clinically significant tissue changes
