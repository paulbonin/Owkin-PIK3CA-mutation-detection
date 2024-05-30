# Owkin-PIK3CA-mutation-detection

Owkin data challenge: https://challengedata.ens.fr/challenges/98
Result presentation: https://docs.google.com/presentation/d/1qGJOGAy_EydOmG7Mcw0OHzWEHvGQTn-9/edit?usp=sharing&ouid=116993149234486675499&rtpof=true&sd=true 

Ranked #1/183 submissions at the date 2023-12-15.

The code was executed on Google Collab. Data is accessible on the challenge website.

----

The challenge proposed by Owkin is a weakly-supervised binary classification problem. Weak supervision is crucial in digital pathology due to the extremely large dimensions images, which cannot be processed as is (100,000 pixels x 100,000 pixels in this case). Each image is called a slide and is given a single binary annotation. For each slide, 1000 smaller images (called tiles) of size 224x224 pixels were extracted in order to reduce data weight.

In this challenge, we aimed to predict whether a patient has a mutation of the gene PIK3CA, directly from a slide.

Below are examples of a full slide (histology slide) and some tiles:

![](images/full_size.png)
![](images/tiles.png)

At the tissue sample scale, our problem is a supervised one as we have mutation data over the whole training set. At the tile scale, the problem is a weakly supervised one as we have one label per bag of tiles.

The data I used were based on the following structure: 

![](images/resnet.png)

From each of the N = 344 slides were extracted 1000 tiles. For each tile, MoCo v2 features were extracted by the Owkin team using a Wide ResNet-50-2 pre-trained on TCGA-COAD. Each feature vector has a length of 2048.
