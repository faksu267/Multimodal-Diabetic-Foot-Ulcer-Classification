# Multimodal-Diabetic-Foot-Ulcer-Classification
A multimodal deep learning framework for classifying Diabetic Foot Ulcer (DFU) stages using fused 4-channel RGB and thermal images.

Description
This repository contains the code and methodology for a multimodal deep learning approach designed to classify Diabetic Foot Ulcer (DFU) stages (Wagner Grades 0 to 5)

Diabetic foot ulcers require continuous monitoring to prevent severe complications such as amputation. To address this, we developed a system that leverages both RGB and Thermal imaging. While RGB images capture textural and morphological changes, thermal images detect hidden heat anomalies caused by inflammation or infection. By combining these two modalities into a single 4-channel tensor, our AI model significantly outperforms single-modality approaches

The framework uses transfer learning with several pre-trained CNN backbones (VGG16, ResNet50, InceptionV3, DenseNet121, EfficientNetV2) and a custom classification head
Evaluated using 5-fold stratified cross-validation, the VGG16-based multimodal (RGB+Thermal) model achieved a peak overall accuracy of 93.25% and a Matthews Correlation Coefficient (MCC) of 91.03%. Additionally, this project outlines a custom Raspberry Pi-based portable image acquisition system (utilizing a Pi Camera V2 and a Flir Lepton 3.5 thermal module), offering a practical infrastructure for in-home telehealth and remote DFU monitoring


Key Features  

  • Multimodal Data Fusion: Combines standard color (RGB) and heat-sensing (Thermal) data into a rich 4-channel input   
  • High Accuracy: Achieved 93.25% overall classification accuracy using a customized VGG16 architecture  
  • Robust Evaluation: Implemented 5-fold stratified cross-validation and class-weighted loss functions to handle dataset imbalance effectively  
  • Hardware Integration: Includes the architectural setup for a low-cost, 3D-printed Raspberry Pi smart monitoring device  
  • Explainable AI (XAI): Utilizes Grad-CAM to visualize the model's focus, proving that the RGB+Thermal fusion correctly targets ulcer sites and clinically significant tissue changes  

## Hardware Setup

To acquire both RGB and thermal images simultaneously, a custom portable imaging system was designed based on the Raspberry Pi architecture. This system provides a practical infrastructure for in-home monitoring and early diagnosis of Diabetic Foot Ulcers (DFU). 

The hardware components used in this prototype include:

*   **Computing Unit:** Raspberry Pi 4B (8GB RAM) .
*   **RGB Sensor:** Raspberry Pi Camera Module V2. It contains an 8-megapixel CMOS sensor capturing full-resolution (3240x2464 pixels) images to preserve detailed textural and color information, connected via the Camera Serial Interface (CSI).
*   **Thermal Sensor:** FLIR Lepton 3.5 Thermal Camera Module. It provides a spatial resolution of 160x120 pixels to detect heat anomalies and is connected via a USB interface.
*   **Display & Control:** Raspberry Pi 7-inch Touchscreen. It is located on the front of the prototype and is used to control the custom Graphical User Interface (GUI) designed for data collection.
*   **Enclosure:** A custom 3D-printed outer casing made from PLA filament.

**System Design & Camera Alignment**
The 3D-printed casing was specifically designed to hold the entire system together and firmly position the RGB and thermal cameras side by side. This physical alignment ensures that both cameras share approximately the same field of view during image acquisition. 

Using the integrated touchscreen, the custom GUI displays real-time thermal and RGB feeds simultaneously. With a single button click, the system triggers both cameras to save the high-resolution RGB image (.jpg), the color-mapped thermal image (.jpg), and the raw thermal temperature matrix (.tiff) into a synchronized folder with a specific timestamp.

<img width="413" height="320" alt="Resim1" src="https://github.com/user-attachments/assets/23c886ec-7740-4171-b9a7-137426c0cf9e" />

## Model Architecture 

The framework utilizes a transfer learning approach to extract deep features from Diabetic Foot Ulcer (DFU) images. Five different Convolutional Neural Network (CNN) architectures pre-trained on the ImageNet dataset were evaluated: ResNet-50, VGG16, DenseNet-121, InceptionV3, and EfficientNetV2. 

To process the multimodal data, the thermal image was added as the fourth channel to the RGB image, converting the input into a 4-channel tensor. Each CNN model's original classification block was removed and replaced with a custom classification head designed for 6-class Wagner staging (Grade 0 to Grade 5).

<img width="1342" height="691" alt="Resim2" src="https://github.com/user-attachments/assets/1bb7c955-83c6-4da2-948e-ab6d78ae1a7d" />

## Experimental Setup and Results

The deep learning models were trained using the PyTorch library on a system equipped with a Ryzen 9 9950X CPU, an NVIDIA RTX 3060 GPU, and 32 GB of RAM. To handle the class imbalance and reliably evaluate the generalization performance, a 5-fold stratified cross-validation method was employed. Additionally, a class-weighted loss function was utilized during training to ensure the model learned all classes in a balanced manner.

Extensive experiments comparing RGB-only, Thermal-only, and Multimodal (RGB+Thermal) datasets revealed that the multimodal approach significantly outperforms single-modality inputs. The **VGG16 architecture** trained with the 4-channel RGB+Thermal dataset achieved the highest overall performance across all metrics.

<img width="941" height="611" alt="Resim3" src="https://github.com/user-attachments/assets/48830b48-3ef3-4673-a9e1-e96faac749f2" />

### Explainability with Grad-CAM

To validate the clinical significance of the model's decisions, Gradient Weighted Class Activation Mapping (Grad-CAM) analysis was performed. The images showed that the model trained with only the thermal dataset could not consistently localize distinct regions at lower stages. In contrast, the model trained with only the RGB dataset successfully captured the wound area and associated tissue regions. On the other hand, the RGB+Thermal (multimodal) model combined the strengths of both models, exhibiting good localization performance for each stage.

<img width="507" height="459" alt="Resim4" src="https://github.com/user-attachments/assets/2365b84c-7d85-4f3f-a1fd-f0f96a6942fb" />

Cite the paper







