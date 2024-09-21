# Image-Colorizer-Project
Repository containing code for colorizing black and white images.

1. Data Preprocessing:

The input images are converted from RGB to LAB color space. The L channel (grayscale) is extracted as input, while the A and B channels (color information) are the target output.
The A and B channels are normalized to be between -1 and 1 for the model.
VGG16 as Feature Extractor:

2. VGG16 as Feature Extractor:

A modified VGG16 model (without the final classification layers) is used to extract features from the grayscale image. The L channel is repeated 3 times to match VGG16's expected input dimensions.
The output from VGG16 is a latent feature map of size (7, 7, 512).

3. Decoder Network:

The decoder takes the VGG16 features as input and progressively upsamples them using Conv2D and UpSampling2D layers.
It predicts the A and B channels for the image, using the tanh activation to match the expected value range.

4. Training:

The model is trained on a dataset for 10,000 epochs to predict the A and B color channels from grayscale input. Mean Squared Error (MSE) is used as the loss function.

5. Colorization:

A function (colorize()) is created to apply the trained model to new test images. It:
- Loads and preprocesses the test image.
- Extracts the L channel and feeds it through VGG16 to get feature maps.
- Uses the decoder to predict the A and B channels.
- Combines the L channel with the predicted A and B channels to form the LAB image.
- Converts the LAB image back to RGB and displays the colorized result.

In summary, this project leverages transfer learning with VGG16 for feature extraction and a custom decoder to colorize grayscale images by predicting their color channels.


## STEPS FOLLOWED 

1. Scrapped flower images from google image search engine.
2. Converted images from RGB to LAB format.
3. Defined a custom deep learning architecture containing encoder and decoder and trained for 15 epochs.
4. Replaced encoder part with VGG16 architecture and trained for 2000 epochs.

## SOME RESULTS OBTAINED (after 2000 epochs)

![Alt text](https://github.com/ChetnaAgarwal/Image-Colorizer-Project/blob/main/result%20snapshots/pic1.png)

![Alt text](https://github.com/ChetnaAgarwal/Image-Colorizer-Project/blob/main/result%20snapshots/pic2.png)

![Alt text](https://github.com/ChetnaAgarwal/Image-Colorizer-Project/blob/main/result%20snapshots/pic3.png)

![Alt text](https://github.com/ChetnaAgarwal/Image-Colorizer-Project/blob/main/result%20snapshots/pic4.png)

![Alt text](https://github.com/ChetnaAgarwal/Image-Colorizer-Project/blob/main/result%20snapshots/pic5.png)

![Alt text](https://github.com/ChetnaAgarwal/Image-Colorizer-Project/blob/main/result%20snapshots/pic6.png)

![Alt text](https://github.com/ChetnaAgarwal/Image-Colorizer-Project/blob/main/result%20snapshots/pic7.png)

PS: More training required for better results...
