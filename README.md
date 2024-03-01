# UniHuman
This repository provides the official code for CVPR 2024 paper UniHuman: A Unified Model For Editing Human Images in the Wild.

## Environment Requirement
Python 3.8

`pip install numpy pillow requests tqdm`

## Data Preparation
We provide the image links of our dataset and their annotations in the zip files. See below for detailed instructions. Please note that we do not own the copyright of the images. It is solely your responsibility to check the original licenses of the images before using them. Any use of the images is at your own discretion and risk.

### Test Data
**Reposing Dataset: WPose**  
1) Download the annotations [wpose.zip](https://drive.google.com/file/d/1vFR5vT8QInP3Zd0D60e0BRZ9c2Trl5bo/view?usp=drive_link) and unzip it under the current directory.
2) Run `python get_wpose_data.py`. This will download and preprocess the raw images. The downloaded images will be stored at `./downloaded_data`, and the preprocessed images will be saved to `./wpose/images`. In our preprocessing pipeline, we crop a rectangle centering the subject in the image and resize its longest side to 1024 pixels.
   
After the above steps, your directory structure should look like
```bash
README.md
get_wpose_data.py
get_wvton_data.py
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
`./downloaded_data`: Downloaded original raw images. The images under the folder are no longer needed once the preprocessing is finished.

`./wpose`: Preprocessed images and annotations.

**Tryon Dataset: WVTON** 
1) Download the annotations [wvton.zip](https://drive.google.com/file/d/1NsTV23n3KDs9eKybE1p8uE7mlSREqlHe/view?usp=sharing) and unzip it under the current directory.
2) Download the clothing images in JPEG format *manually* using the urls provided in `./wvton/clothing_urls.txt`. Put these clothing images in a new folder named `./cl_downloaded_data`. Do NOT change the file names of the downloaded clothing images.
3) Run `python get_wvton_data.py`. This will download the human images and preprocess all images. The downloaded human images will be stored at `./downloaded_data`. The preprocessed images will be saved at `./wvton/images` and `./wvton/clothes`. In our preprocessing pipeline, we crop a rectangle in the image and resize its longest side to 1024 pixels.
   
After the above steps, your directory structure should look like
```bash
README.md
get_wpose_data.py
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
`./downloaded_data`: Downloaded original raw human images. The images under the folder are no longer needed once the preprocessing is finished.

`./cl_downloaded_data`: Downloaded original raw clothing images. The images under the folder are no longer needed once the preprocessing is finished.

`./wvton`: Preprocessed images and annotations.

### Training Data

**L-40K**

- [x] OOD test data release.
- [ ] L-40K traininig data release.
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
