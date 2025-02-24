# efficient_video_generation
## 0 History
### Early Exploration
**VDM** stands as the pioneer, which extends the conventional image diffusion 
U-Net architecture to a 3D U-Net structure and employs joint training with both images and videos

conditional sampling technique
requires paired video-text datasets


**Make-A-Video** introduces a novel paradigm. 
Here, the network learns visual-textual correlations from paired image-text data
and captures video motion from unsupervised video data. This innovative approach reduces the
reliance on data collection, resulting in the generation of diverse and realistic videos. Furthermore, by
employing multiple super-resolution models and interpolation networks, it achieves higher-definition
and frame-rate generated videos.

### Temporal Modeling Exploration
**MagicVideo** stands as one of the earliest works to employ the Latent Diffusion Model
(LDM) for T2V generation in latent space. By utilizing diffusion models in a lower-dimensional
latent space, it significantly reduces computational complexity, thereby accelerating processing speed.
The introduced frame-wise lightweight adaptor aligns the distributions of images and videos so that
the proposed directed attention can better model temporal relationships to ensure video consistency.

**LVDM** also employs the LDM [193] as its backbone, utilizing a hierarchical
framework to model the latent space. By employing a mask sampling technique, the model becomes
capable of generating longer videos. It incorporates techniques such as Conditional Latent Perturbation and Unconditional Guidance to mitigate performance degradation in the later stages of
auto-regressive generation tasks. With this training approach, it can be applied to video prediction
tasks, even generating long videos consisting of thousands of frames.

**VideoFactory** introduces a swapped cross-attention mechanism to facilitate interaction
between the temporal and spatial modules, resulting in improved temporal relationship modeling.
Besides, trained on its proposed HD-VG-130M dataset, the approach presented in the paper is capable
of generating high-resolution videos at (1376 × 768) resolution.

**ModelScope** incorporates spatial-temporal convolution and attention into LDM for
T2V tasks. It adopts a mixed training approach using LAION and WebVid, and serves as
an open-source baseline method.

Previous methods predominantly rely on 1D convolutions or temporal attention to establish
temporal relationships. **Latent-Shift**, on the other hand, focuses on lightweight temporal modeling.
Drawing inspiration from TSM, it shifts channels between adjacent frames in convolution
blocks for temporal modeling. Additionally, the model maintains the original T2I capability
while generating videos.

### Multi-stage T2V methods
**Imagen Video** extends the T2I model, Imagen [198], for video
generation using a cascaded video diffusion model composed of seven sub-models: one for base
video generation, three for spatial super-resolution, and three for temporal super-resolution. This
three-stage training pipeline employs T2I techniques like classifier-free guidance [84], conditioning
augmentation [83], and v-parameterization [201]. Progressive distillation techniques [159, 201]
are used to speed up sampling time, making these multi-stage training techniques effective for
high-definition video generation

Concurrently, **Video LDM** trains a T2V network composed of three training stages, including
key-frame T2V generation, video frame interpolation and spatial super-resolution modules. It adds
temporal attention layer and 3D convolution layer to the spatial layer, enabling the generation of
key frames in the first stage. Subsequently, through the implementation of a mask sampling method,
a frame interpolation model is trained, extending key frames of short videos to higher frame rates.
Lastly, a video super-resolution model is employed to enhance the resolution.






## 1 Parameter-Efficient Method

### 1.1 ControlNets
[description](controlnet.md)

### 1.2 Adapters
[description](adapter.md)
1. SimDA: Simple Diffusion Adapter for Efficient Video Generation
[paper](https://openaccess.thecvf.com/content/CVPR2024/papers/Xing_SimDA_Simple_Diffusion_Adapter_for_Efficient_Video_Generation_CVPR_2024_paper.pdf)
[code](https://github.com/ChenHsing/SimDA)
![img_1.png](img_1.png)
    devises a parameter-efficient training approach by maintaining the parameter of the T2I model and uses two adapters to train it.
2. I2V-Adapter: A General Image-to-Video Adapter for Diffusion Models
[paper](https://arxiv.org/pdf/2312.16693)
3. CTRL-Adapter: An Efficient and Versatile Framework
for Adapting Diverse Controls to Any Diffusion Model
[paper](https://arxiv.org/pdf/2404.09967) [code](https://github.com/HL-hanlin/Ctrl-Adapter)
4. X-Adapter: Adding Universal Compatibility of Plugins for Upgraded Diffusion Model
[paper](https://showlab.github.io/X-Adapter/static/Paper/X_Adapter_Arxiv.pdf)
[code](https://github.com/showlab/X-Adapter)







### 1.3 Low Rank Adaption

1. AnimateDiff
2. DragVideo
3. MagicStick

## 2 Efficient Sampling and Inference

### 2.1 Training Free Method

### 2.2 Training Based Method


## 3 Efficient Architecture
U-Net, DiT, U-ViT, MamBa

## 4 Current Video Genaration Models
### 4.1 Text-to-video Generation
CogVideo

CogVideoX

MagicVideo: employ Latent Diffusion Model for T2V generation

Imagen Video
![img.png](img.png)

ControlVideo

Control-A-Video

StoryDiffusion

Ctrl-Adapter

Animate Anymore

Make-A-Video: the network learns visual-textual correlations from paired image-text data and captures video motion from unsupervised video data
ideoFu
Latent-Shift: focuses on lightweight temporal modeling

### 4.2 Image-to-video Generation
1. ***AnimateDiff:*** Animate Your Personalized Text-to-image Diffusion Models without Specific Tuning [[Paper]](https://openreview.net/pdf?id=Fx2SbBgcte) [[Project]](https://animatediff.github.io/)

## 5 Preference Optimization
