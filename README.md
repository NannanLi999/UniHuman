# UniHuman
This repository provides the official code for CVPR 2024 paper UniHuman: A Unified Model For Editing Human Images in the Wild.

## Download Data
We provide the image links of our dataset in the zip files. See below for detailed instructions. Please note that we do not own the copyright of the images. It is solely your responsibility to check the original licenses of the images before using them. Any use of the images is at your own discretion and risk.

### Test Data
**WPose**  
1) Download the annotations `wpose.zip` and unzip it under the current directory.
2) Download the images **at the original resolution** to the folder `downloaded_data` using the links provided in `ood_test_reposing/image_urls.txt`.
3) Run `python get_wpose_data.py` to preprocess the raw images. In our preprocessing pipeline, we crop a rectangle centering the subject in the image, resize its longest side to 1024 pixels, and then pad the image with white pixels to size 1024x1024.
After the preprocessing, your directory structure should look like
```bash
.
├── downloaded_data
├── ood_test_reposing
    ├── image_urls.txt
    ├── rename.txt
    ├── bbox.txt
    ├── test_pairs.txt
    ├── test_data.pkl
    ├── images
    ├── densepose
    ├── gt_parsing
```
`downloaded_data`: Downloaded original raw images.

`ood_test_reposing/image_urls.txt`: Image links.

`ood_test_reposing/rename.txt`: Each row is a pair of (image new name, raw image name).

`ood_test_reposing/bbox.txt`: Bounding box coordinates in the original raw images. 

`ood_test_reposing/test_pairs.txt`: Test image pairs of the same subject in different poses.

`ood_test_reposing/test_data.pkl`: A list of processed image paths and captions. Each entry is a dictionary like `{source: ood_test_reposing/images/1.png, source pose: ood_test_reposing/densepose/1.png, prompt:..., seg: ood_test_reposing/gt_parsing/1.png, target: ood_test_reposing/images/2.png, target pose: ood_test_reposing/densepose/2.png, }`

`ood_test_reposing/images`: Processed images.

`ood_test_reposing/densepose`: Densepose predictions of the processed images.

`ood_test_reposing/gt_parsing`: Ground truth parsing maps of the processed images. We use these parsing maps for all the comparison methods in our paper.

**WVTON** 


### Training Data

**L-40K**

- [ ] OOD test data release.
- [ ] L-40K traininig data release.
- [ ] Inference code release.
- [ ] Training code release.
  
## Citation
Please cite our paper if you use the dataset in your work.
`
@InProceedings{Li_UniHuman_2024,
    author    = {Nannan Li, Qing Liu, Krishna Kumar Singh, Yilin Wang, Jianming Zhang, Bryan A. Plummer, Zhe Lin},
    title     = {UniHuman: A Unified Model For Editing Human Images in the Wild},
    booktitle = {CVPR},
    year      = {2024},
}
`

## License
This dataset is released under [Adobe Research License](https://github.com/adobe-research/EntitySeg-Dataset/blob/main/LICENSE.md). The license prohibits commercial use and allows for non-commercial research use.
