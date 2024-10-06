# Indian Classical Dance Style Classification CNN

This project uses a Convolutional Neural Network (CNN) to classify images of Indian classical dance forms. The goal is to identify various dance styles, such as Bharatanatyam, Kathak, Kathakali, Kuchipudi, Manipuri, Mohiniyattam, Odissi, and Sattriya, from the given dataset of images. The model is trained using transfer learning with the VGG16 architecture and fine-tuned to recognize eight distinct Indian classical dance styles. *Achieved 86% final test identification accuracy.*

## Project Structure

The code provided consists of the following sections:

1. **Data Setup**: The dataset is assumed to be stored in a Kaggle directory, and the data is categorized into training and testing folders. Initially, images are loaded from the dataset, and corresponding directories for each dance form are created.

2. **Data Splitting**: The images are split into training and testing sets using an 85-15 ratio. The function `split_data()` is used to randomly assign images into the training and testing directories.

3. **Transfer Learning with VGG16**: The pre-trained VGG16 model, which is trained on ImageNet, is used as the base model. The top layers are replaced with custom dense layers to fit our dataset, and the model is trained on images resized to 156x156.

4. **Image Augmentation**: Image augmentation is used to increase the variability of the training set by applying transformations such as rotation, shift, shear, zoom, and horizontal flipping.

5. **Training the Model**: The model is compiled using the RMSprop optimizer and trained using the training and validation data generators. The learning rate is reduced dynamically during training if the validation accuracy plateaus.

6. **Prediction on Test Data**: The model is used to predict the dance form for images in the test dataset. The predictions are saved in a CSV file named `submission_dance.csv`.

## Model Training

- **Architecture**: The pre-trained VGG16 model is used as the feature extractor, with the top fully connected layers replaced by new layers suitable for classification.
- **Fine-Tuning**: The first 17 layers of the VGG16 model are frozen, and the remaining layers are fine-tuned to learn the nuances of Indian dance styles.
- **Training Parameters**: The model is compiled with the RMSprop optimizer and a learning rate of 0.001. A callback (`ReduceLROnPlateau`) is used to reduce the learning rate when the validation accuracy does not improve.

## Author

This notebook was created for research purposes at Emory University to classify Indian classical dance forms using transfer learning and convolutional neural networks.
