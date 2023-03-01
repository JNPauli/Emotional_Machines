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

## 17.01.2023
other dimensions that pleasure dominance (color)

semantic?

attention network, salience maps. where do people look?. [example 1](https://sci-hub.se/10.1109/tmm.2018.2830098),
[example 2](https://arxiv.org/pdf/1904.09146.pdf%C2%A0%E8%8B%A5%E6%9C%89%E4%B8%AA%E4%BA%BA%E8%AF%AF%E5%8C%BA%E5%8F%8A%E7%BF%BB%E8%AF%91%E9%94%99%E8%AF%AF%EF%BC%8C%E6%81%B3%E8%AF%B7%E5%8F%8A%E6%97%B6%E8%AF%84%E8%AE%BA%E6%8C%87%E6%AD%A3%E3%80%82),
[example 3](http://wrap.warwick.ac.uk/123588/1/WRAP-deep-salient-object-detection-contextual-guidance-Han-2019.pdf)

BSP:
Objects features(Alexnet) last layer switch with valence. (Kim paper, VI. C)

TODO:
Neuromatch
Alexnet train

## 18.01.2023
Dataset = Emotic

Model = CNN, based on the model architecture from Kim et al. and Kosti.
    Compare continous measures with SVR and/or linear regression
    Compare continous measures with SVM and/or logistic regression?
    
Inputs = 
    Color (pleasure, dominance, arousal)
    Object features (AlexNet, VGG16, and ResNet)
    Facial expression (if possible)
    Body poes
    salient object detection / Attention networks?


Research questions:
    Which features are actually important -> Similar to incremental validity
    Vision: Input to protect app: Output -> Category and valence.


## 01.03.2023
Started to load images and annotations into CSV by following the [Pytorch implementation](https://github.com/Tandon-A/emotic) of the emotic dataset.

Applied Alexnet on some images to extract the objects. It worked in principle, but the classifications are only sort of right. I tried to use YOLO, but it gives me an error. Maybe cloud computation will solve this. Not so sure.

Looked in different ways to compute emotion for given color. [See](https://d1wqtxts1xzle7.cloudfront.net/40230224/CS-Nijdam-Niels-libre.pdf?1448097609=&response-content-disposition=inline%3B+filename%3DCS_Nijdam_Niels.pdf&Expires=1677666186&Signature=giaS7-kW5FpY2daK9gf-Gucy9FdzlabzeWwuecdvqFBrEgVBQKTpGMJxfCzTcMO2BU4DAXAES4JJebivkpAnycEM9uXdZDx2SeCh07R34Qv6Gbr48xIeIGIFdHrkojzNd2n3tuMp5aAQmMoSxnCoz0YbyxEQaAQTeRB-KjJk4lkXwX4B2K9T52is8dJcow3-nVLgG~9TjrXrB~1KeKxUm3-N2uBz9HElflCUy-VnXPmkZbX2mDw9q9~61i73i2p5BRd2vXrEbvxXgLOqZ~Ko9EIbvkEUour9AIeQ4PYNJSYwo82MBrxvNnyUGDrdcKGOiedtGnbkqUjFwKNRS-2n2g__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA), especially page *5*.

Further investigates salience maps. Seems doable! [Notable resource](https://github.com/sunnynevarekar/pytorch-saliency-maps/blob/master/Saliency_maps_in_pytorch.ipynb) and the respective [paper](https://arxiv.org/pdf/1312.6034.pdf).


