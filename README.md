# UniHuman
This repository provides the official code for CVPR 2024 paper UniHuman: A Unified Model For Editing Human Images in the Wild.

## Environment Requirement
Python 3.8

`pip install numpy pillow requests tqdm`

## Data Preparation
We provide the image links of our dataset and their annotations in the zip files. See below for detailed instructions. Please note that we do not own the copyright of the images. It is solely your responsibility to check the original licenses of the images before using them. Any use of the images is at your own discretion and risk.

| Dataset | No. of Train Images | No. of Test Pairs | 
| --- | --- | --- |
| WPose | N/A | 2304 |
| WVTON | N/A | 440 |
| LH-400K | 409,270 | N/A |

### Test Data
**Reposing Dataset: WPose**  

![ ](/assets/wpose.png)

1) Download the annotations [wpose.zip](https://drive.google.com/file/d/1vFR5vT8QInP3Zd0D60e0BRZ9c2Trl5bo/view?usp=drive_link) and unzip it under the current directory.
2) Run `python get_wpose_data.py`. This will download and preprocess the raw images. The downloaded images will be stored at `./downloaded_data`, and the preprocessed images will be saved to `./wpose/images`. In our preprocessing pipeline, we crop a rectangle centering the subject in the image and resize its longest side to 1024 pixels.
   
After the above steps, your directory structure should look like
```bash
get_wpose_data.py
downloaded_data
wpose
  ├── README
  ├── image_urls.txt
  ├── bbox.txt
  ├── test_pairs.txt
  ├── test_data.pkl
  ├── images
  ├── densepose
  ├── parsing
```
`./downloaded_data`: Downloaded original raw images. The images under this folder are no longer needed once the preprocessing is finished.

`./wpose`: Preprocessed images and annotations.

**Tryon Dataset: WVTON** 

<img src="assets/wvton.png" height="300">

1) Download the annotations [wvton.zip](https://drive.google.com/file/d/1NsTV23n3KDs9eKybE1p8uE7mlSREqlHe/view?usp=sharing) and unzip it under the current directory.
2) Download the clothing images in JPEG format *manually* using the urls provided in `./wvton/clothing_urls.txt`. Put these clothing images in a new folder named `./cl_downloaded_data`. Do NOT change the file names of the downloaded clothing images.
3) Run `python get_wvton_data.py`. This will download the human images and preprocess all images. The downloaded human images will be stored at `./downloaded_data`. The preprocessed images will be saved at `./wvton/images` and `./wvton/clothes`. In our preprocessing pipeline, we crop a rectangle in the image and resize its longest side to 1024 pixels.
   
After the above steps, your directory structure should look like
```bash
get_wvton_data.py
cl_downloaded_data
downloaded_data
wvton
  ├── README
  ├── image_urls.txt
  ├── clothing_urls.txt
  ├── bbox.txt
  ├── clothing_bbox.txt
  ├── test_pairs.txt
  ├── test_data.pkl
  ├── images
  ├── clothes
  ├── clothes_mask
  ├── densepose
  ├── parsing
  ├── mmpose_clothes
  ├── mmpose_human
```
`./downloaded_data`: Downloaded original raw human images. The images under this folder are no longer needed once the preprocessing is finished.

`./cl_downloaded_data`: Downloaded original raw clothing images. The images under the folder are no longer needed once the preprocessing is finished.

`./wvton`: Preprocessed images and annotations.

**Other Public Datasets**

See [VITON-HD](https://github.com/shadow2496/VITON-HD), [DressCode](https://github.com/aimagelab/dress-code) and [DeepFashion-Multimodal](https://github.com/yumingj/DeepFashion-MultiModal).

### Training Data

**LH-400K**

![ ](/assets/lh-400k.png)

1) Download the annotations [lh-400k.zip](https://drive.google.com/file/d/1zZZVjH7CNy1qI5ychHMZ_Kh1LjR5Q6PT/view?usp=sharing) and unzip it under the current directory.
2) Run `python get_laion_data.py`. This will download and preprocess the raw images. The preprocessed images will be stored at `./lh-400k/images`. In our preprocessing pipeline, we resize the image's longest side to 512 pixels.
   
After the above steps, your directory structure should look like
```bash
get_laion_data.py
lh-400k
  ├── README
  ├── image_urls.txt
  ├── train_data.pkl
  ├── images
  ├── densepose
  ├── parsing
```

At the time of releasing this dataset, 408,520 image urls are still valid.


### TODO

- [x] OOD test data release.
- [x] L-40K traininig data release.
- [ ] Inference code release.
- [ ] Training code release.
  
## Citation
Please cite our paper if you use the dataset in your work.
```
@InProceedings{Li_UniHuman_2024,
    author    = {Nannan Li, Qing Liu, Krishna Kumar Singh, Yilin Wang, Jianming Zhang, Bryan A. Plummer, Zhe Lin},
    title     = {UniHuman: A Unified Model For Editing Human Images in the Wild},
    booktitle = {CVPR},
    year      = {2024},
}
```

## License
This dataset is released under [Adobe Research License](https://github.com/adobe-research/EntitySeg-Dataset/blob/main/LICENSE.md). The license prohibits commercial use and allows for non-commercial research use.
