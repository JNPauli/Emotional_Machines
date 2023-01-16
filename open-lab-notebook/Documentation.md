# This document serves the purpose of documenting the progress made in the project for my master thesis.

## 25.11.2022
As for now, the rough idea of the master thesis is the following:
We have a set of images, that depict situations in which game/internet addicting or social behavior can be seen. Within the set of game/internet addicting behavior, we want humans to rate the emotional valence of those pictures. This rating will be compared with the rating of machine learning algorithms. As for now, I found one [pretrained network](https://github.com/rkosti/emotic) by Kosti et al. (2017) that rates the emotional valence of an image, in respect to context. Ideally, we will use more than one machine learning approach to asses valence. In [this paper by Kim et al., 2017](https://arxiv.org/pdf/1705.07543.pdf) they did something similar and used linear regression and support vector regression to tackle the problem. This would be an intersting approach, since the first model introduced from Kosti et al. is a CNN. 

## 10.12.2022
The notebook has not been updated in a while, because I invested a lot of time in literatur research. Image classification can be done by using a SVM. Interesting resources are the following: [1](https://medium.com/analytics-vidhya/image-classification-using-machine-learning-support-vector-machine-svm-dc7a0ec92e01), [2](https://nikolasent.github.io/classifier/2017/08/01/Image-classification-using-SVM.html). 

Idea #1 would be to use an SVM approach for creating a set of game addiction vs non game addiction behavior.

Idea #1.1 would be the following:
I think it would be a nice idea to use the pretrained network and compare it to the SVR. Maybe I can even create a new CNN? 

Also I have been thinking about the research question. Im not sure, if comparing the performance of the machine learning models with the performance of humans is a good idea. My doubts come from the fact, that the input to f.e. the SVR are ratings made by humans. I still think it is a nice idea to compare the performance of several machine learning models with one and another. 

Also:
How large is the stimuli set? Because we need to define a **training set**, **validation set** and **test set**. We can split the stimulus set in three parts, if its large enough.

I would suggest to create a research question this month, so we can schedule a meeting with Maren to discuss how to proceed.

My first draft would be the following: Comparing different machine learning techniques in their performance on detecting emotional valence in game disorder images.
While there are already some studies that focus on valence recognition in images, this has not been done with a set of game disorder images yet. This master thesis could thus add some novelty in the field of research, by adding the context of game disorder. While I would like to maybe even investigate a different clinical context (for example, Images that promote eating disorder habits) it is probably easier for now to stick to the given set of stimuli.

In this thesis I would #1 use a SVM to classify the given image stimuli into game addiction vs non game addiction behavior and #2 let a sample of students rate the images in regard to the respective valence. This serves as an input to the SVR and the pretrained CNN.

## 13.12.2022
It looks like one approach we could use is the one proposed by [Kim et al. (2017)](https://arxiv.org/pdf/1705.07543.pdf).
Extract from the images the following features:
The object, the face (if visible, this would be the novel component) and background features (color-,local and semantic features). The extracted features serve as the input to the prediction of the valence in the images. 
While this has been done in a given stimulus set, we would add novelty by a) the game-disorder context and b) the optional face recogniton. 
Features extracted from face recognition, combined with the context, has already been done by [Lee et al. (2019)](https://openaccess.thecvf.com/content_ICCV_2019/papers/Lee_Context-Aware_Emotion_Recognition_Networks_ICCV_2019_paper.pdf) but he solely used faces as the main object.

The extracted features can then be used at the input to the SVR to predict the emotional valence.

The emotional valence relates is important in regard to gaming disorder, because it can be argued, that a certain "dysfunctional" behavior still needs to be examined in respect to the emotionality. 

## 14.12.2022
Notes from the meeting:
Probably go with another Dataset, so do not use the game disorder dataset. The sample size of the stimulus set is probably to low. 
Canidates for now are the [EMOTIC](http://sunai.uoc.edu/emotic/) or the [CAER](https://caer-dataset.github.io/download.html) database.

Updated goal of the master thesis is to apply a CNN, that combines different architecture elements from the CNN's listed in the respective papers, (see Kosti, Kim, Lee paper) to one of those datasets.

The network from Kosti and colleagues did not consider the facial expression, because the EMOTIC database containts ~25%images without visible faces. It would be interesting to apply the CNN from Kosti on the CAER database. One research question might be, how important the facial expression is in the detection of emotions, as compared to other markers, as defined by kosti et al.

## 07.01.2023
So I downloaded the Dataset used by Kim et al (2018) and started to explore it (see data/Dataset_Exploration.ipynb).
Two dimensions were rated for the image stimuli: Valence and arousal. In the EMOTIC dataset there were several categories used, but also three continuous dimensions called Valence, Arousal and and Dominance. Kosti and colleagues used a different CNN structure than Kim and colleagues. One possible idea for the master thesis would be to apply the CNN structure from Kosti to the Kim dataset and see, how it can be compared in regard to the two dimensions "Valence" and "Arousal".

Additionally, it would be nice to incoperate a facial expression framework. However, not on every image a face can be seen. And im not sure, if this exceeds the time and computing resources.

## 12.01.2023
Ideas:
Split the emotic dataset in images, so we only have images that contain faces.
Next, establish a new CNN model architecture. 
The main features that should be part of the CNN: 
Extracting facial expression cues ([like in the CAER-net-s](https://caer-dataset.github.io/file/JiyoungLee_iccv2019_CAER-Net.pdf)). In general: Crop face and apply CNN layers on it?!
Extract body pose
Semantic features
color features

Categorize and use continuous dimensions.
Maybe compare the continuous predictions with SVR and/or linear regression? Similiar to [Kim et al., 2018](https://arxiv.org/pdf/1705.07543.pdf).

I think it is not a bad idea to have the predictive view that this can be applied to the Protect App Stimuli. I think all features in the proposed architecture could be benefitial to the project. Maybe the idea could be to train it on the emotic dataset and another thesis could use this model and apply it to protect app stimuli?

## 15.01.2023
Also I was wondering if I can really use the Kim et al. dataset? Does it not have to carry a license or something like this?
I like the idea of applying a similar structure like the one from the Kim paper and apply it to the emotic database.

Building the model with tensorflow? 
How does classification work, when building a new model?

Vision: Input to protect app: Output -> Category and valence.

Also: Some features are extracted with Alexnet and so forth. How can I adapt my own CNN, so the features do not have to be extracted from alexnet and then be put into the model? Meaning it is "ready to use".

How do I train my model on the emotic dataset? Dont I have to adapt the structure then?