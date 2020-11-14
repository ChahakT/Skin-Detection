
# Skin-Detection

The appearance of skin in an image depends on the illumination conditions (illumination geometry and color) where the image was captured. Therefore, an
important challenge in skin detection is to represent the color in a way that is invariant or at least in sensitive to changes in illumination. The choice of the color space affects greatly the performance of any skin detector and its sensitivity to change in illumination conditions.

The human skin color has a restricted range of hues and is not deeply saturated, since
the appearance of skin is formed by a combination of blood (red) and melanin (brown,
yellow). Therefore, the human skin color does not fall randomly in a given color space,
but clustered at a small area in the color space. But it is not the same for all the color
spaces. Variety of color spaces have been used in skin detection literature with the aim
of finding a color space where the skin color is invariant to illumination conditions. The
choice of the color spaces affects the shape of the skin class, which affects the
detection process.

A different class of color spaces are the orthogonal color spaces used in TV
transmission. This includes YUV, YIQ, and YCbCr . YIQ is used in NTSC TV broadcasting
while YCbCr is used in JPEG image compression and MPEG video compression.All these
color spaces separate the illumination channel (Y) from two orthogonal chrominance
channels (UV,YIQ, YCbCr ). Therefore, unlike RGB, the location of the skin color in the
chrominance channels will not be affected by changing the intensity of the
illumination


**Training Pseudocode**


train_s = list for (RGB, YCC,HSV values) skin pixels in training set


train_ns = list for non skin pixels in training set


Loop for all images in training set:


Give path; Read the original image; Read the ground truth image


Threshold the ground truth image to make skin pixels white and rest black


Read height, width, channels in original image


Loop for all pixels in Image in raster scan manner:


Read BGR pixel value; Convert to appropriate colour space; Write converted values to a list

If (pixel classification =skin):Append 1 Else: Append 0


**Testing Pseudocode**

test_s= list for (RGB, YCC,HSV values) skin pixels in test set

test_ns = list for non skin pixels in test set

Loop for all images in test set :

Give path of test set; Read the original image; Read the ground truth image

Threshold the ground truth image to make skin pixels white and rest black

Read height, width, channels in original image

Loop for all pixels in Image in raster scan manner:

Read BGR pixel value; Convert to appropriate colour space; Write converted values to a list

If (pixel classification =skin): Append 1 Else: Append 0


train=train_s+train_ns

test= test_s+test_ns

Define mean of numbers; Define standard deviation of numbers

Define summarize: It calculates Mean and Variance of each attribute in dataset
summaries =Dictionary to contain mean and variance of all components in both
training and test set.

summaries[0]= summarize(train_s); summaries[1]= summarize(train_ns)

pr_s= Prior Probability of skin pixels; pr_ns= Prior Probability of non_skin pixels

pr=[pr_s,pr_ns]

Define calculate Probability = It calculates probability of x given gaussian distribution
with mean and variance

Define calculateClassProbabilities = Calculates probability of feature vector x given
mean and variance of training set = prior * likelihood

Define predict = If posterior for skin is more than that of non_skin it classifies as 1 else
0

Define predictions = gets predictions for entire test set

Define getAccuracy = gets accuracy for test set



**Testing on non Test Image**

Read the Image

Plot the Image

Loop for all pixels in Image in raster scan manner:

Read BGR pixel value

Convert to appropriate colour space

Write converted values to a list

Get predictions for this test set.

Rearrange in raster scan manner and plot the binary output.
