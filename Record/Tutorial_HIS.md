# Hyperspectral-Image-Super-Resolution

本节主要回顾与整理HIS（高光谱超分辨率）工作. **如果有重要的工作未能涵盖在里面，请随时联系我. If you find that important resources are not included, please feel free to contact me.**   

Hyperspectral image super-resolution is a kind of technique that can generate a high spatial and high spectral resolution image from one of following observed data:   
+ low-resolution multispectral image e.g. LR RGB
+ high-resolution multispectral image e.g. HR RGB
+ low-resolution hyperspectral image
+ high-resolution multispectral image + low-resolution multispectral image  


According to kind of observed data, hyperspectral image super-resolution techniques can be divided into four classes,  Note that we take hyperspectral image reconstruction from 2D measurement as a class of SSR:
+ spatiospectral super-resolution (SSSR)
+ spectral super-resolution (SSR)
+ single hyperspectral image super-resolution (SHSR)
+ multispectral image and hyperspectral image (MHF)

============================================================================================
## Image Quality Measurement

####  Peak Signal to Noise Ratio (PSNR)
PSNR 峰值信噪比，是一种客观的图象质量评估方法，用来测量图象与原图之间的噪声差异值。**PSNR数值越大，则
噪声水平或者失真程度越低，PSNR值越小则表示恢复图象与原图差别越大** , PSNR应该要大点 
$$PSNR = 10\times \log_{10}{\frac{max_{I}^{2} }{mse}}$$
其中, $mse=\frac{1}{W\times H}(I_{1}-I_{2})$, $W$和$H$分别是图象的长和宽,$max_{I}^{2}$是图象的最大像素值，如1或255.

####  Root Mean Square Error (RMSE)

#### Structural SIMilarity index (SSIM)
SSIM 结构相似性指数，是度量两张图片相似性的客观指标。SSIM的输入是两张图片相似性的客观指标。SSIM的输入是两张图象，输出的是两张图象的相似性，具体计算如下
$$SSIM(I_{1},I_{2} ) = \left [ l\left (I_{1},I_{2} \right) \right ] ^\alpha \left [ c\left (I_{1},I_{2}   \right )  \right ] ^\beta \left [  s\left (I_{1},I_{2}   \right )\right ] ^\gamma $$
$$l\left (I_{1},I_{2} \right) = \frac{2\mu_{1}\mu_{2}+c_{1} }{\mu_{1}^2+\mu_{2}^2+c_{1}}$$
$$c\left (I_{1},I_{2} \right) = \frac{2\sigma_{I_{1}I_{2}}+c_{2}}{\sigma_{I_{1}}^2+\sigma_{I_{2}}^2+c_{2}}$$
$$s\left (I_{1},I_{2} \right) = \frac{2\sigma_{I_{1}I_{2}}+c_{3}}{\sigma_{I_{1}I_{2}}+c_{3}}$$
其中 $l\left (I_{1},I_{2} \right)$ 是输入 $I_{1},I_{2}$ 的**亮度比较**， $c\left (I_{1},I_{2} \right)$ 是**对比度比较**， $s\left (I_{1},I_{2} \right)$ 是**结构比较**，
 $\mu$ 分别代表 $I_{1},I_{2}$ 的标准差， $\sigma$ 分别代表 $I_{1},I_{2}$ 的协方差，其他参数为参数防止出现分母为零带来的错误。
####  Spectral Angle Mapper (SAM)
光谱角映射，SAM，是一种基于映射的方法对光谱图象的相似性度量的方法，可以看作SAM计算的是两个向量之间的相似性。SAM仅为高光谱图象的评价指标，自然图像的评价指标不能使用SAM。SAM用于
度量原始高光谱数据与重建高光谱数据之间的光谱相似性，其单位为度或者弧度。具体在高光谱图像中，是在图象中所有像素上计算SAM，然后求平均值,计算公式如下：  
$$SAM\left ( I_{1},I_{2}  \right )= \arccos\left ( \frac{\left \langle  I_{1},I_{2}  \right \rangle }{I_{1}I_{2}} \right )$$
the latex is SAM\left ( I_{1},I_{2}  \right )= \arccos\left ( \frac{\left \langle  I_{1},I_{2}  \right \rangle }{\left \|  I_{1} \right \|_{2}\left \|  I_{2} \right \|_{2}} \right )

#### Erreur Relative Globale Adimensionnelle de Synthèse (ERGAS)
相对无量纲全局误差，ERGAS表示恢复的图象和原始图象之间的相似程度，**融合光谱质量越高，ERGAS越小**，当为0的时候，计算方法如下：
$$ERGAS=\frac{100}{R}\sqrt{\frac{1}{B}\sum_{b}^{}\left ( \frac{RMSE(b)}{\mu(b)}  \right )^2   }$$
其中，R是超分辨的倍数，B为u=高光谱图象的波段数目， $\mu(b)$ 表示的是波段b的平均值，RMSE(b)为波段b与原始图象相应波段之间均方根误差。
#### Universal Image Quality Index (UIQI)


============================================================================================
# Related Works
In our research, we focus on Multi-spectral image and hyperspectral image which based on Deep Learning based Approaches. We records related work as followed: \\
+ Deep Hyperspectral Image Sharpening TNNLS2018 [Coding_tf](https://github.com/renweidian/DHSIS)  [pdf](https://drive.google.com/file/d/1FIyVL9c8jlDY3heEZ57nGvpSDZc0mkeT/view?usp=drive_open)
+ Unsupervised Sparse Dirichlet-Net for Hyperspectral Image Super-Resolution CVPR2018 [Coding_tf](https://github.com/aicip/uSDN)  [pdf](https://arxiv.org/abs/1804.05042)
+ Deep Hyperspectral Prior: Denoising, Inpainting, Super-Resolution, arXiv2019 [Coding_torch](https://github.com/acecreamu/deep-hs-prior)[pdf](https://arxiv.org/abs/1902.00301)
+ Multispectral and Hyperspectral Image Fusion by MS/HS Fusion Net, CVPR2019, [Coding_tf](https://github.com/XieQi2015/MHF-net)  [pdf](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://arxiv.org/pdf/1901.03281.pdf)
+ Deep Blind Hyperspectral Image Super-Resolution, IEEE TNNLS 2020, [Coding_torch](https://github.com/JiangtaoNie/DBSR)  [pdf](https://ieeexplore.ieee.org/abstract/document/9136736)
+ Unsupervised Adaptation Learning for Hyperspectral Imagery Super-Resolution, CVPR2020, [Coding_torch](https://github.com/JiangtaoNie/UAL)  [pdf](https://openaccess.thecvf.com/content_CVPR_2020/html/Zhang_Unsupervised_Adaptation_Learning_for_Hyperspectral_Imagery_Super-Resolution_CVPR_2020_paper.html)
+ Cross-Attention in Coupled Unmixing Nets for Unsupervised Hyperspectral Super-Resolution, ECCV2020, [Coding_torch](https://github.com/danfenghong/ECCV2020_CUCaNet)
+ Unsupervised Recurrent Hyperspectral Imagery Super-Resolution Using Pixel-Aware Refinement, TGRS2021, [Coding_torch](https://github.com/JiangtaoNie/Rec_HSISR_PixAwaRefin)  [pdf](https://ieeexplore.ieee.org/document/9292466)
+ Hyperspectral Image Super-Resolution via Deep Progressive Zero-Centric Residual Learning, TIP2021, [Coding_mat](https://drive.google.com/drive/folders/1esPuiKcSEzQBeDPMg_IU_VvB3FvH0aZl)
+ Hyperspectral Image Super-Resolution via Deep Prior Regularization with Parameter Estimation, IEEE TCSVT 2021, [Coding_torch](https://github.com/xiuheng-wang/Sylvester_TSFN_MDC_HSI_superresolution/blob/main/train.py)
+ Hyperspectral Image Super-Resolution with Self-Supervised Spectral-Spatial Residual Network
+ Model-Guided Deep Hyperspectral Image Super-Resolution, IEEE TIP 2021, [Coding_torch](https://github.com/chengerr/Model-Guided-Deep-Hyperspectral-Image-Super-resolution)
+ Hyperspectral Image Super-resolution with Deep Priors and Degradation Model Inversion,  ICASSP 2022
+ Model Inspired Autoencoder for Unsupervised Hyperspectral Image Super-Resolution, TGRS 2022, [Coding_torch](https://github.com/liuofficial/MIAE)



