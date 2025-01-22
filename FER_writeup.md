Maia Piechocki
piechock@usc.edu

1. Introduction: 
This model is a CNN made with 4 blocks of convolutional layers to classify 7 emotions, achieving a maximum accuracy of 54.61%.

2. Dataset:

This model uses Kaggle's FER2013 dataset containing 2 folders(train and test) and 7 classes. The data consists of 48x48 pixel grayscale images of faces. 
I chose these preprocessing steps based on the need to improve the model's performance and generalization. Rescaling the images ensures that all 
pixel values are on a consistent scale, which helps the optimizer converge efficiently. Data augmentation(horizontal flips, zooming, rotating, and shifting) 
was applied to expand the dataset, helping the model generalize better by exposing it to more variations of the images.
Finally, I split the dataset into 80% training and 20% validation to avoid overfitting while ensuring the model was trained on enough data.
The preprocessing techniques were chosen to provide as much diversity for the CNN model to learn from and the train/validation split was found most optimal after experimenting with different ratios.

4. Model Development and Training:

The model consists of four blocks of convolutional layers followed by ReLU activation, batch normalization, max pooling, and dropout to reduce overfitting.
I used the Adam optimizer with an exponential learning rate decay to ensure the model converges smoothly while adapting the learning rate as training progresses. 
I experimented with different learning rate decay strategies, such as exponential decay and step decay, and tested different learning rate initializations (0.001, 0.0005) to stabilize training and improve convergence. 
The batch size was set to 64 after experimenting with smaller and larger batch sizes, and I initially trained for 80 epochs but reduced it to 50 after observing that the model started to converge early.
I also implemented early stopping and model checkpoint callbacks to save the best model and prevent overfitting. These adjustments, along with data augmentation (rotation, zoom, shift), helped fine-tune the training procedure and optimize the model's performance for multi-class image classification.

5. Model Evaluation/results

The model achieved an overall accuracy of 54.61%.
Loss indicates the error between the predicted and actual values = 1.3248
Recall was calculated to assess how well the model identifies positive samples = 0.1415
F1-Score combines both precision and recall into a single metric = 0.1352
These results indicate a decent balance between precision and recall, but there is still significant room for improvement.

6. Discussion

a) The dataset, model architecture, and training procedures fit well for multi-class image classification of the dataset, with data augmentation enhancing generalization, and the Adam optimizer, early stopping, and model checkpoints 
ensuring efficient training.
b) Yes, this approach can be extended to various domains that involve image classification, such as security applications (facial recognition or surveillance), medical imaging, or land-pattern monitoring and detection. 
The primary challenge was improving performance, as the model's accuracy was 54.61%, with low recall and F1-score, indicating the need for better handling of class imbalance and improving the identification of positive samples. 
While data augmentation helped with generalization, the model still struggled to correctly classify certain emotion categories, most likely due to the complexity of emotion recognition in images. Also, there were discrepancies in numbers of images per class.
For example, the class 'happy' had 1774 images, while 'disgust' had only 111 images. Supplementing lacking training data for specific classes could improve performance. 
c) In the future, I plan to address the issue of class imbalance, possibly by using class weighting or oversampling techniques. Also, I would explore TL with ViT, which would probably enhance classification results. 
By applying transfer learning with a pre-trained ViT model, I can fine-tune the network on my dataset, potentially improving recall and F1-score, and further optimizing the model’s ability to generalize for applications
in fields like security or even medical imaging and environmental detection and monitoring. 