## Face Generation GAN based on DCGAN architecture


### Architecture
![DCGAN Architecture](dcgan.png?raw=true "DCGAN Architecture")

### Examples
#### Mnist
![MNIST](samples/mnist.png?raw=true "MNIST Sample")

#### Celeba
![Celeba](samples/celeba.png?raw=true "Celeba Samples")
![Celeba](samples/celeba2.png?raw=true "Celeba Samples")

### Details

**codes for layers**

- **1 layer** = (size)F|C(ks,str,p)|DC(ks,str)|BN|D|LR
- **(size):** size of layer or filters
- **F:** Fully Connected
- **C:** Convulution 
- **DC(ks,str):** Deconvulution with (Kernel Size, Stride, padding)
- **BN:** Batch normalization
- **D:** Dropout
- **LR:** Leaky Relu

### Generator:

#### Full: (7x7x1024)F -> D -> LR
#### DCONV1: (512)DC(3,2,same) -> BN -> D -> LR  
#### DCONV2: (256)DC(3,2,same) -> BN -> D -> LR 
#### DCONV3: (128)DC(5,1,same) -> BN -> D -> LR
#### DCONV_OUT: (channles)DC(5,1)

### Discriminator:

#### CONV1: (64)C(5,1,valid) -> LR
#### CONV2: (128)C(5,1,valid) -> BN -> D -> LR
#### CONV3: (256)C(5,1,valid) -> BN -> D -> LR
#### CONV4: (512)C(5,2,valid) -> BN -> D -> LR
#### OUT: (flat)F

### Hyperparameters for celeba set
- Leaky Relu Slope: 0.2
- Adam Optimizaer beta: 0.5
- Learning rate: 0.0003
- Batch Size: 16
- latent vector dimension: 100
- dropout: 0.5
- 1 epoch
