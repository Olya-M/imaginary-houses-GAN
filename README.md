# imaginary-houses-GAN


Moving through the latent space for epoch 10300:
* gif here



Here is what the average generated looks like for the same epoch:




While most of the houses don't end up looking entirely viable, here are some images that I thought looked pretty cool:



* Epoch 4350
I think this might be my favorite epoch
idk-4


* Epoch 8100


* Epoch 10075


* Epoch 10300
 
 
## Training data:
While I initially tried scraping images of fantasy houses from online, I found cleaning up the received images took up too much time. In the end, the dataset consists of 1028 manually collected images, primarily drawings, of fantasy or fantasy-like houses from subreddits like [r/imaginarydwellings]( https://old.reddit.com/r/ImaginaryDwellings/), [r/imaginaryarchitecture]( https://old.reddit.com/r/ImaginaryArchitecture/), [r/imaginarylibraries]( https://old.reddit.com/r/ImaginaryLibraries/), and google searches such as “fantasy cabin”, “fantasy tavern inn”, “flying house fantasy” and so on in February of 2021. To make sure that houses don’t get cropped out during training, I manually cropped the images in the dataset so that houses are near the center of each image.
This dataset can be found **here**

Example of a training batch:
*trainingbatcheg


A thousand images is a small dataset for a GAN, so the model was first pretrained for 30 epochs on a combined dataset of the imaginary houses images and ~12,500 images from a [Houses Prices and Images – SoCal dataset](https://www.kaggle.com/ted8080/house-prices-and-images-socal). Images of the inside of houses or images without clear single houses were removed.


# Training:

The model itself is a standard deep convolutional general adversarial model (DCGAN) built with Pytorch. Some key points are that it uses [DiffAugment](https://github.com/mit-han-lab/data-efficient-gans) data augmentation, [Spectral normalization](https://github.com/christiancosgrove/pytorch-spectral-normalization-gan) for the discriminator, and an [AdaBelief](https://juntang-zhuang.github.io/adabelief/) optimizer. I have tried using a Wasserstein GAN but haven't had success with it when generating 256x256 images of imaginary houses.
**weights for epochs 30, 4350, and 10300 can be found...**

### Training video:
After the first 30 epochs, each progress image is from every 5th epoch.
Warning: the video might have some flashes, especially near the beginning
*vid


Losses:


Scores:


