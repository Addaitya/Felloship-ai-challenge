# Computer Vision Challenge: Flower Classification



## Problem Statement



## Approach


1. **Data Preparation:** 
The images were resize to 224 by 224 size
2. **Data Augmentation:** Data augmenation technique is employed for generalisation and impove on problem like class imbalace dataset.
3. **Trasfer Learning**
I applied two transfer learning appoaches:
<br> 3.1 **Finetuning**: Performed finetuning by retraining the last 10 layers of the pre-trained ResNet 50 model on the Flowers dataset. I was able to achieve **80 percent** of test accuracy. Training beyond that leads to overfitting.
<br> 3.2 **Feature Extraction**: I removed the top classification layer of the model. Then applied custom classification layer(softmax layer). So here only last classification layer is finetune, weights of whole ResNet 50 remain frezzed. I was able to achieve **82 percent** of test accuracy

4. **Training and Optimization:** I trained the model using the training set and monitored its performance on the validation set. Data augmentation technique is used to improve generalization and prevent overfitting.

## Dataset
The Dataset give is Oxford 102 flowers dataset.

**Image count:** 8190

**Images per class:** 40-200. This is amount is very less for doing trasfer learning so this is why data augmenation technique is used.

Labeling: Labels were give from 1 to 102. The names for the flower were taken from one gist file.

## Data Visalisation
### Flower Image of each class


![flower of each class](https://raw.githubusercontent.com/Addaitya/Felloship-ai-challenge/refs/heads/main/images/flowers.png)

### Distrubustion of example for each Classe

First Graph: Trainig data. As you can is the image are imbalance for each class.

Second Graph: Validation data(10 images per class)

Third Graph: Test data(10 images per class)

![Image count for each flower class](https://raw.githubusercontent.com/Addaitya/Felloship-ai-challenge/refs/heads/main/images/example_distribution.png)



## Analysis of Height and width of images
![Image height and width analysis](https://github.com/Addaitya/Felloship-ai-challenge/blob/main/images/height_width.png?raw=true)


### Training stat for finetuned model
![finetuned model accuracy analysis](https://github.com/Addaitya/Felloship-ai-challenge/blob/main/images/finetuning.png?raw=true)
### Training stat for  feature extraction model
![feature extraction model accuracy analysis](https://github.com/Addaitya/Felloship-ai-challenge/blob/main/images/feature_extraction.png?raw=true)
## Challenges Faces
- **Overfitting**: Main issue was the model was getting overfitting ie i was getting training accuracy of about 99 percent and validation accuracy of about 92 percent. To solve this challenge i added Batch Normalisation layer and drop out layer for better generalisation.
- **Data Augmentation**: Added multiple data augmenation layer to get more veriety to model and it generalise well during training.
- **No of Epoch to use**: High epoche lead to overfitting. By experimentation i found 5 epoche for finetuning trasfer learing method and 10 epoche for feature extractoin trasfer learning provide generalise model.
