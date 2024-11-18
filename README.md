# Personalized Privacy Protection Mask Against Unauthorized Facial Recognition

![](assets/intro-git.png)
Face recognition (FR) can be abused for privacy intrusion. Governments, private companies, or even individual attackers can collect facial images by web scraping to build an FR system identifying human faces without their consent. This paper introduces Chameleon, which learns to generate a user-centric personalized privacy protection mask, coined as P3-Mask, to protect facial images against unauthorized FR with three salient features. First, we use a cross-image optimization to generate one P3-Mask for each user instead of tailoring facial perturba- tion for each facial image of a user. It enables efficient and instant protec- tion even for users with limited computing resources. Second, we incor- porate a perceptibility optimization to preserve the visual quality of the protected facial images. Third, we strengthen the robustness of P3-Mask against unknown FR models by integrating focal diversity-optimized en- semble learning into the mask generation process. Extensive experiments on two benchmark datasets show that Chameleon outperforms three state-of-the-art methods with instant protection and minimal degrada- tion of image quality. Furthermore, Chameleon enables cost-effective FR authorization using the P3-Mask as a personalized de-obfuscation key, and it demonstrates high resilience against adaptive adversaries.

For more technical details and experimental results, we invite you to check out our paper [[here]](https://www.ecva.net/papers/eccv_2024/papers_ECCV/papers/10846.pdf):
* Ka-Ho Chow, Sihao Hu, Tiansheng Huang, and Ling Liu, "Personalized Privacy Protection Mask Against Unauthorized Facial Recognition," European Conference on Computer Vision (ECCV), Milan, Italy, Sep. 29-Oct. 4, 2024.
```text
@inproceedings{chow2024chameleon,
  title={Personalized Privacy Protection Mask Against Unauthorized Facial Recognition},
  author={Chow, Ka-Ho and Hu, Sihao and Huang, Tiansheng and Liu, Ling},
  booktitle={European Conference on Computer Vision},
  year={2024}
}
```

## Python Environment
This repository is implemented with Python 3.7. You can create a virtual environment and install the required libraries with the following command:
```commandline
pip install -r requirements.txt
```
You should use a CPU backend to launch Chameleon. GPU acceleration will be enabled soon.

## Privacy Protection with Chameleon
1. Download the preprocessed LFW dataset and pretrained FR models, unzip them, and place the `data` and `weights` folders under the root directory as follows:
```
.
├── data     <--------------------
│   ├── faces
│   │   └── ...
│   └── bboxes.pkl
├── weights  <--------------------
│   └── ...
├── core
│   └── ...
├── models
│   └── ...
├── utils
│   └── ...
├── main.py
├── requirements.txt
└── README.md
```
2. Run Chameleon with the following script:
```commandline
python main.py
```
3. By default, it will protect Morena Baccarin by using her facial images. You should expect the output as follows:
```commandline
Epoch 1 / 50 - [L↓: -0.3480] FEAT↑: 0.3480 | DSIM↓: 0.0020 | SSIM: 0.9960: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 21/21 [01:52<00:00,  5.34s/it]
Epoch 2 / 50 - [L↓: -1.2221] FEAT↑: 1.2221 | DSIM↓: 0.0123 | SSIM: 0.9755: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 21/21 [01:53<00:00,  5.39s/it]
Epoch 3 / 50 - [L↓: -1.9540] FEAT↑: 1.9582 | DSIM↓: 0.0284 | SSIM: 0.9431: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 21/21 [01:52<00:00,  5.33s/it]
Epoch 4 / 50 - [L↓: -2.1474] FEAT↑: 2.3390 | DSIM↓: 0.0356 | SSIM: 0.9288: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 21/21 [01:52<00:00,  5.33s/it]
Epoch 5 / 50 - [L↓: -2.4406] FEAT↑: 2.5368 | DSIM↓: 0.0374 | SSIM: 0.9253: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 21/21 [01:53<00:00,  5.38s/it]
...
 
```
4. You can locate the privacy protection mask at `./outputs/Morena_Baccarin/jpg`. It includes the mask generated at each epoch.

|        Epoch 0         |        Epoch 2         |        Epoch 4         |                Epoch 6 |                Epoch 8 | Epoch 10                |
|:----------------------:|:----------------------:|:----------------------:|-----------------------:|-----------------------:|-------------------------|
| ![](assets/epoch0.jpg) | ![](assets/epoch2.jpg) | ![](assets/epoch4.jpg) | ![](assets/epoch6.jpg) | ![](assets/epoch8.jpg) | ![](assets/epoch10.jpg) |

## Acknowledgement
This project is developed based on the following repositories:
* [Shawn-Shan/fawkes](https://github.com/Shawn-Shan/fawkes) 