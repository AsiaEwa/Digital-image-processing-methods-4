# Digital-image-processing-methods-4
## Types of noise and image filtering methods

Gaussian noise is the most common noise when recording images using cameras and camcorders. This is related to thermal noise of the matrices (CCD matrices are particularly susceptible to this phenomenon) and imperfections in the matrices' workmanship.

![image](https://github.com/AsiaEwa/Digital-image-processing-methods-4/assets/101841759/1ec5d5af-b2d9-4c8c-b55d-88846b9e1004)

 Orginal and with noise.
 
Salt and pepper noise occurs when extreme pixel values appear in random places in the image. In the case of a black and white image, these are black and white dots resembling scattered grains of pepper and salt. For a color image, such interference appears as randomly occurring extreme values of a given component.

![image](https://github.com/AsiaEwa/Digital-image-processing-methods-4/assets/101841759/576aea75-3a32-4bab-a36d-8cd400eaa59a)

Speckle noise is defined as multiplicative noise, most often arising during the recording of coherent light. In particular, this applies to satellite and radar images, ultrasound images and optical coherence tomography. This noise is created as a result of random interference of rays returning from strongly scattering media.

![image](https://github.com/AsiaEwa/Digital-image-processing-methods-4/assets/101841759/cd22b343-0c79-48fc-b037-49b377c65e35)

Poisson noise is an indispensable element of image recording using photodetectors. It arises as a consequence of discretization during light registration. This is noise described by a normal distribution.
![image](https://github.com/AsiaEwa/Digital-image-processing-methods-4/assets/101841759/76636f64-1c03-4045-ac08-7f7b685c56a5)

Low-pass filters suppress noise and image details (high-frequency elements, while low-frequency elements are passed through. This type of filters are used to reduce the amount of noise and to blur and smooth the image.

![image](https://github.com/AsiaEwa/Digital-image-processing-methods-4/assets/101841759/c8c98c33-b362-44bf-86cd-c71211b4f33d)

averaging filter - is a basic low-pass filter. Averages values based on the values of its own cell and immediately adjacent cells. To reduce the blur effect, this filter is modified by increasing the weight of the central point

square filter – works similarly to the averaging filter, with the difference that the square filter averages the values based on the values of a given cell and 24 neighbors. As a result of this action, more details are filtered out than in the case of an averaging filter,

circular filter – works similarly to the square filter, with the difference that the circular filter averages the values based on the values of a given cell and 20 neighbors. Values from the corners do not participate in the filtration process.

Gaussian – the distribution of weights in a Gaussian filter resembles a solid shape similar to the normal distribution curve. The values decrease as you move away from the central point. The Gaussian filter mask can be of different sizes.

High-pass filters attenuate low-frequency elements while allowing and amplifying elements such as noise and fine details (high-frequency elements).

![image](https://github.com/AsiaEwa/Digital-image-processing-methods-4/assets/101841759/ce550d62-a686-4462-b099-31a4380dd116)

mean removal - this is a popular version of the high-pass filter. Using this filter significantly sharpens the image. A common problem with this type of filtration is noise amplification.

* H1 – The example high-pass filter, compared to the mean removal filter, sharpens the image less and does not emphasize the noise in the image as much.
* H2 – An example of a high-pass filter, compared to the mean removal filter and H1, does not emphasize the noise in the filtered image as much.

Assessment of filtration quality In order to make an assessment, a measurable parameter should be used that can be clearly compared in order to select the objectively best filtration for a given filter type.

Such a parameter may be the peak signal-to-noise ratio (PSNR). In image processing, this parameter is typically used to determine the lossy compression quality of an image. If we add noise in a controlled manner and then the noisy image is filtered, we can compare the input image before noise and the output image. To calculate PSNR, the mean squared error (MSE) must first be calculated.

Original image, no noise:

![image](https://github.com/AsiaEwa/Digital-image-processing-methods-4/assets/101841759/bd125dea-fb00-4829-b8af-dbf6f9f892ac)

1. Gaussian noise - additive Gaussian noise with an average value of 0 and a given variance  2, use the function

J = imnoise(I,'gaussian')

![image](https://github.com/AsiaEwa/Digital-image-processing-methods-4/assets/101841759/f721a42e-75b8-4bb3-83b8-a7da0dfbeef4)

2. "Salt and pepper" noise with equal share of both ingredients,

J = imnoise(I,'salt & pepper')

![image](https://github.com/AsiaEwa/Digital-image-processing-methods-4/assets/101841759/359c1ce0-560b-4506-8440-4089316a9cdb)

3. Additive Poisson noise,

J = imnoise(I,'poisson')

![image](https://github.com/AsiaEwa/Digital-image-processing-methods-4/assets/101841759/e5abf59f-bb66-4168-abb0-49fed9334d9b)

4. "speckle" - multipeak speckle noise with a standard Gaussian distribution,

J = imnoise(I,'speckle')

![image](https://github.com/AsiaEwa/Digital-image-processing-methods-4/assets/101841759/55e452ec-cce4-4cb0-aa07-ad899789317d)

Filtering using low pass filters:

1. Average filter
2. Gaussian filter
3. Circular Filter
4. Square Filter

PSNR - peak signal to noise ratio [db-decibels]
the ratio of the maximum signal power to the power of the noise disturbing this signal, usually expressed in decibels.

![image](https://github.com/AsiaEwa/Digital-image-processing-methods-4/assets/101841759/10a1cdd4-5c5a-4d7f-9ad0-8c9fc0c26d01)

For Gaussian noise, the averaging filter performs best, PSNR = 27.5945.
For Salt and Pepper noise, a circular filter presents itself; PSNR = 26.8058.
For Poisson noise, a Gaussian filter presents itself; PSNR = 31.8335.
For Speckle noise, a circular filter presents itself; PSNR = 27.1337.
Analyzing the results, it seems that Poisson noise is the easiest to filter, for each filtering and Poisson noise was the best filtered.

Filtering using high pass filters:

1. Mean removal filter
2. H1 filter
3. H2 filter
4. own high pass filter (HP2)

![image](https://github.com/AsiaEwa/Digital-image-processing-methods-4/assets/101841759/ce89cd21-ba4f-4634-96e0-4630cea78f9d)

For Gaussian noise, the H2 filter achieved the highest PSNR result: PSNR = 17.9195.
For the Salt and Pepper noise, the H2 filter achieved the highest PSNR result: PSNR = 18.3657.
For Poisson noise, the H2 filter achieved the highest PSNR result: PSNR = 24.8851.
For Speckle noise, the H2 filter achieved the highest PSNR result: PSNR = 16.7514.
The least distorted image was generated for Poisson noise and the H2 filter.
The worst results were for Speckle noise, while the best results were for Poisson noise.

![image](https://github.com/AsiaEwa/Digital-image-processing-methods-4/assets/101841759/c6c7153c-5d69-45be-963b-84a07101d5d6)

The best set of filters according to the PSNR index was adopted by Gaussian filters with an H2 filter, generating a result of 32.0208.
The Gaussian low-pass filter could be considered the best filter for processing, as its results outperformed the best results compared to other filters. The exception was the mean removal filter, in which the circular filter generated the best result.
