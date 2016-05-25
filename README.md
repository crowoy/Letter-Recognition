# Letter-Recognition
Fourier Feature Analysis - Classifying letters [S,T,V] based on features in the Fourier Space - uses Nearest Neighbour and MLE classifiers

## Goal
Given `10` sample images of drawings of the letters `[S,T,V]`, can a classifier be made to correctly identify a test image of an `[S,T,V]` as the correct letter.

## Idea
Use features extraction in the Fourier Space in order to gain same knowledge about the different letters. The use these features on the training data, and tweak them to classify the letters correctly. Finally, create test images, and see how well the classifier works.

## Classification Results
Below is the trained 1<sup>st</sup> nearest neighbour classifier (using the training samples):

![Classifier 1](https://raw.githubusercontent.com/crowoy/Letter-Recognition/master/res/classifier1.png?token=ACEgQstLVTVh65ClKrEwRBx4RhftlsT_ks5XT0bGwA%3D%3D)

## Training Images
The `10` training images for `[S,T,V]` that were used to train the classifier can be found here:

https://github.com/crowoy/Fourier-Feature-Extraction/tree/master/src/trainingSamples

## Test Images
I decided to create `6` images for each letter, and see how the trained classifier worked with them. Below are the training images I created, and how they classified the letters:

![S Test](https://raw.githubusercontent.com/crowoy/Letter-Recognition/master/res/S_test.png?token=ACEgQhyVnU-_kVVQ0oj8uy-QZHA2Jbz-ks5XT0b_wA%3D%3D)
![T Test](https://raw.githubusercontent.com/crowoy/Letter-Recognition/master/res/T_test.png?token=ACEgQvkmwySbCwp7sHCVRPZgbaPMEbFkks5XT0cBwA%3D%3D)
![V Test](https://raw.githubusercontent.com/crowoy/Letter-Recognition/master/res/V_test.png?token=ACEgQjv238_tdCsbfFfYWTmRqasXDO5Yks5XT0cDwA%3D%3D)

![Classifier 2](https://raw.githubusercontent.com/crowoy/Letter-Recognition/master/res/classifier2.png?token=ACEgQlJOhbf7n4lDTORZ8pBYFx6rEMljks5XT0ctwA%3D%3D)

## Testing Other Letters
After this, I decided to test to see how the classifier worked on letters which it wasn't meant to classify. For this, I took `2` images, one of an `A` and one of a `B`.
For these results, please look at the report: https://github.com/crowoy/Fourier-Feature-Extraction/blob/master/Report/oc14771.pdf

## Using a Differnt Classifier (MLE)
I thought it would interesting to see how another classifier worked on all of the same data. A Maximum Likelihood Estimator (MLE) classifier was implemented. Here are the results (the lines represent the decision boundaries):

![MLE Classifier](https://raw.githubusercontent.com/crowoy/Letter-Recognition/master/res/MLE.png?token=ACEgQv5IT7QGsaZ2_LzsmCViS4qM_CXiks5XT0cvwA%3D%3D)

***

# How?

### Feature Extraction (Fourier Analysis)
The first process I performed was a Fourier Transform on all the test images. Here is an average of each of the letters' Fourier Spaces:

![Fourier Space Average](https://raw.githubusercontent.com/crowoy/Letter-Recognition/master/res/FS_avg.png?token=ACEgQnCFnuuS11KSz28xKaLtyAoJvY6gks5XT0dMwA%3D%3D)

The next step was extracting features from the Fourier Space. I decided to only extract using 2 filters (i.e. in 2 dimensions). Below are the filters I used:

Mask 1 | Mask 2
------------ | -------------
![Mask 1](https://raw.githubusercontent.com/crowoy/Letter-Recognition/master/res/mask1.png?token=ACEgQl0ER2FyGhM4OjlDUNRsU9rvj4bLks5XT0dkwA%3D%3D) | ![Mask 2](https://raw.githubusercontent.com/crowoy/Letter-Recognition/master/res/mask2.png?token=ACEgQplgdx7jdoatOdhTe4hNd3c66aBrks5XT0dmwA%3D%3D)

This resulted in the following being extracted from the Fourier Spaces (I also applied a treshold value to further eliminate values from the Fourier Space):

![Mask 1 Applied](https://raw.githubusercontent.com/crowoy/Letter-Recognition/master/res/appliedMasks1.png?token=ACEgQiqIT9WePTe7mlv_ayiPQZzSz4gfks5XT0dowA%3D%3D)
![Mask 2 Applied](https://raw.githubusercontent.com/crowoy/Letter-Recognition/master/res/appliedMasks2.png?token=ACEgQjIqSlHJJX3acl07W44Hsz5BmBgrks5XT0dqwA%3D%3D)

I then summed these values other each of the Fourier Spaces, and these resulted in the values for the `x` (Mask 1) and `y` (Mask 2), which were then plotted.

### Other Letters?
So there is obviously the potential to expand this further (e.g. more than simply `3` letters, different languages, words, etc...). However, after what I have done now, the process of expanding does not require any additional knowledge or problem solving skills, when taking this  approach (i.e. it would simply involve adding better, more specific, masks, more training data, more dimensions). 

It would not be possible to use these masks with every English letter and achieve a good general classifier.

# Dependencies
- Python
- Jupyter Notebook
- Training and Test Data
