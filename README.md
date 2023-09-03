# SR-GAN
This is pytorch implementation of Super Resolution Gan which enhances the resloution of input images (given they were low resolution) to higher resolution.
The dataset used is taken form kaggle and its consists of 12k high resolution images, i transformed these images into low-res and high-res images using torch transforms
here highres has 4 times thep pixel count of lowres.#I could have used the original images as target but using them would be too taxing on the limited hardware.
![sample of training data after transformation in comparision with original , lowres(input), highres(target)](https://user-images.githubusercontent.com/26987970/265220544-12fc01f0-af86-4aec-a8c3-f84e98f6ca46.png)
![sample 2](https://user-images.githubusercontent.com/26987970/265220587-3a3ea551-104f-4cf1-8feb-96f5d8651696.png)

The model architecture consists of Convolution block, Upsampling block, Dense-residual block repeated and connnected to form Generator and Discriminator just usees conv blocks with increasing channels.
![model architecture of sr gan]

Loss function for generator L1 loss, VGG loss, Adversarial loss --> gen_loss = l1_loss + loss_for_vgg + adversarial_loss
for discriminator is a combination of Gradient penalty and mean loss.

#Training
Model was trained on 12k images for 131 epochs with batch size of 16 and implementing pytorch mixed precision for improved performance in training time.
these are the results i got, could be better with more epochs and training with higher-res target images.
![sample of input low res](https://user-images.githubusercontent.com/26987970/265220830-f9fd3eb7-9585-4b8f-b9e4-8dca2339261b.png)
![sample output high res](https://user-images.githubusercontent.com/26987970/265220856-2cdb3a20-9077-455d-ab8d-f1f90b1bbeee.png)
