# Lesson 11 - Fourier Transform

**DEF:** ```Natural Images have similar power spectrum, so what really maters to reconstruct the image is the phase.```

### Ringing - Process of reducing high frequency in an image
Spurious signals near sharp transitions in a signal. This effect is caused by distortion or loss of high frequency information in image.
The term "ringing" is because the output signal oscillates at a fading rate around a sharp transition in the input
Many phenomenon like Gibbs Phenomenon( you can’t approximate sharp edges in images very well) are caused due to that

**DEF:** ```Convolution in spatial domain is the multiplication in frequency domain and vice-verse.```
``` Convolution in spatial domain is the multiplication in frequency domain and vice-verse.
         Spatial Domain         Frequency Domain
           g = f * h               G = F x H
           g = f x h               G = F * H

TERMS: * = convolution and x = multiplication

NOTE: If f and h is too large? It is when we use Fourier Trasform.
TERMS
           g   =   f   *   h 
           |       |       |
         [IFT]    [FT]    [FT]
           |       |       |
           G   =   F   x   H
         
TERMS: FT = Fourier Transform and IFT = Inverse Fourier Transform        
```
**DEF:** ```Sall Gaussian in space have a big Gaussian in frequency and vice-verse.```

**DEF:** ``` The Fourier Transform of a Gaussian is a Gaussian. ```
         ``` The Fourier Transofrm of an inpulse train is an inpulse train. As they get bigger in space they get close in frequency.```


# Aliasing - Signals travelling in desguise as other signals (frequencies).
```
e.x: An airplane propeler spinning forward but when we look it is spinning backwards. This is because the high frquency and low frequency can not be distinguished.
```

**DEF:** ``` Sampling is the multiplication of a signal by a comb.```

**DEF:** ``` Image sub-sampling is throwing away rows and columns to create a 1/2 size picture.```
```
NOTE: AS the image shrinks aliasing (image definition worsening) starts happening. In other to reduce alising Gaussian filtering helps.
By using Gaussian (lowpass) pre-filtering image aliasing is reduced.
```

**IMPORTANT - DEF:** ``` The higher the frequency the less sensity human visual system is. by Campbell-Robson```

**IMPORTANT Note** JPEG uses Block-Based Discrete Cosine Transform (DCT) on 8x8

















