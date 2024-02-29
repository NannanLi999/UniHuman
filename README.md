# UniHuman
This repository provides the official code for CVPR 2024 paper UniHuman: A Unified Model For Editing Human Images in the Wild.

## Environment Requirement
Python 3.8

`pip install numpy pillow requests`

## Download Data
We provide the image links of our dataset in the zip files. See below for detailed instructions. Please note that we do not own the copyright of the images. It is solely your responsibility to check the original licenses of the images before using them. Any use of the images is at your own discretion and risk.

### Test Data
**WPose**  
1) Download the annotations `wpose.zip` and unzip it under the current directory.
2) Run `python get_wpose_data.py` to download and preprocess the raw images. The downloaded images will be stored at `downloaded_data`, and the preprocessed images will be saved at `wpose/images`. In our preprocessing pipeline, we crop a rectangle centering the subject in the image and resize its longest side to 1024 pixels.
   
After the above steps, your directory structure should look like
```bash
.
get_wpose_data.py
├── downloaded_data
├── wpose
    ├── image_urls.txt
    ├── bbox.txt
    ├── test_pairs.txt
    ├── test_data.pkl
    ├── images
    ├── densepose
    ├── gt_parsing
```
`downloaded_data`: Downloaded original raw images. The images under the folder are no longer needed once the preprocessing is finished.

`wpose/image_urls.txt`: Image links.

`wpose/bbox.txt`: Bounding box coordinates in the original raw images. 

`wpose/test_pairs.txt`: Test image pairs of the same subject in different poses.

`wpose/test_data.pkl`: A list of processed image paths and captions. Each entry is a dictionary like `{source: wpose/images/1.png, source pose: wpose/densepose/1.png, prompt:..., seg: wpose/gt_parsing/1.png, target: wpose/images/2.png, target pose: wpose/densepose/2.png, }`

`wpose/images`: Processed images.

`wpose/densepose`: Densepose predictions of the processed images.

`wpose/gt_parsing`: Ground truth parsing maps of the processed images. We use these parsing maps for all the comparison methods in our paper.

**WVTON** 


### Training Data

**L-40K**

- [ ] OOD test data release.
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
