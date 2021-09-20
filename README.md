# Imaginary Houses GAN
This is a DCGAN Jupyter notebook for generating 512x512 imaginary fantasy houses.

#### Moving through latent spaces:

https://user-images.githubusercontent.com/68296887/133906699-251b9a60-7be8-4059-a34d-bb5a87bbac21.mp4

 
## Training data:
I collected 1028 images, primarily drawings, of fantasy or fantasy-like houses from subreddits such as [r/imaginarydwellings]( https://old.reddit.com/r/ImaginaryDwellings/), [r/imaginaryarchitecture]( https://old.reddit.com/r/ImaginaryArchitecture/), [r/imaginarylibraries]( https://old.reddit.com/r/ImaginaryLibraries/), and Google searches such as “fantasy cabin”, “fantasy tavern inn”, and “flying house fantasy”. The images were collected in February of 2021. I initially webscraped the images, but I found that removing duplicates and unclear images was taking up more time than manual data collection. I chose the images so that there was only one or two houses (or a combined housing unit) featured in the image. To make sure that houses didn't get cropped out during training, I pre-processed the images so that houses are near the center of each image. To assure data cleanliness, I also cropped out text and watermarks. 

A thousand images is a very small dataset for a GAN, so I first pretrained the model for 30 epochs on a combined dataset of the imaginary houses images and ~12,500 images from a [Houses Prices and Images – SoCal dataset](https://www.kaggle.com/ted8080/house-prices-and-images-socal). I removed images of insides of homes as well as images without clear individual houses.


## Training:
The model is a convolutional general adversarial model (DCGAN) built with Pytorch. Some key points are that it uses [DiffAugment](https://github.com/mit-han-lab/data-efficient-gans) data augmentation, [Spectral normalization](https://github.com/christiancosgrove/pytorch-spectral-normalization-gan) for the discriminator, and an [AdaBelief](https://juntang-zhuang.github.io/adabelief/) optimizer. I tried out a Wasserstein loss for generating 256x256 images but haven't found it to work well with the fantasy houses dataset. The training took about a week and a half with a laptop RTX 2060.

## Sample outputs:

##### An average batch of outputs from the model:

![Average batch](https://user-images.githubusercontent.com/68296887/133906728-17f2242a-839a-498e-96ff-40d5bb03ebcb.png)


##### Here are a few houses that I thought looked pretty neat:

##### Epoch 4350:

![4350_1](https://user-images.githubusercontent.com/68296887/133907170-78d5fc62-2481-4ba6-94f2-e3c25ff16919.png)

![4350_2](https://user-images.githubusercontent.com/68296887/133907251-190ad90e-d823-4097-8d4e-cddefb37b005.png)


##### Epoch 8100:

![8100_1](https://user-images.githubusercontent.com/68296887/133907285-178b655f-0421-436c-b57f-0034cf95a95d.png)

![8100_2](https://user-images.githubusercontent.com/68296887/133907299-052ebe67-882e-4e51-8889-b9d27b869eb9.png)


##### Epoch 10300:

![10300_1](https://user-images.githubusercontent.com/68296887/133907411-f6420bd7-adf7-41e7-805e-19115a489a6c.png)

![10300_2](https://user-images.githubusercontent.com/68296887/133907458-4116b9ca-472a-4d4f-880c-474433586ade.png)

![i0300_3](https://user-images.githubusercontent.com/68296887/133907432-cb15fc07-e1ab-41d6-86af-e2b3defd9ca5.png)

![10300_4](https://user-images.githubusercontent.com/68296887/133907467-40d97ad8-c4ed-4b68-b121-698bc063b9af.png)

![10300_5](https://user-images.githubusercontent.com/68296887/133907483-9723a411-4083-4bcf-82b0-170abe0686a4.png)
