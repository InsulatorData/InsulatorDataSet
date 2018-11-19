# Insulator Data Set - Chinese Power Line Insulator Dataset (CPLID)
Provide normal insulator images captured by UAVs and synthetic defective insulator images.

    
    @article{tao2018detection,
      title={Detection of Power Line Insulator Defects Using Aerial Images Analyzed With Convolutional Neural Networks},
      author={Tao, Xian and Zhang, Dapeng and Wang, Zihao and Liu, Xilong and Zhang, Hongyan and Xu, De},
      journal={IEEE Transactions on Systems, Man, and Cybernetics: Systems},
      year={2018},
      publisher={IEEE}
    }
This dataset is divided into two part:

- `Normal_Insulators` contains the normal insulators capture by UAVs. The number of the normal insulator images is **600**.


- `Defective_Insulators` contains the insulators with defect. The number of the defective insulator images is **248**. Since we don't have too much defective insulators, the data augmentation method is applied. These images are synthesized by following process:
    - Use the algorithm in [TVSeg](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.154.6237) to segment the defective insulator from a small part original images, the segment results are the mask images;
    - Use affine transform to augment the original images and their mask, the augmentation results is a lot of original-mask image pairs;
    - Use these image pairs to train the [U-Net](https://link.springer.com/chapter/10.1007/978-3-319-24574-4_28);
    - Use the trained U-Net to segment the rest part of images;
    - Attach the insulators in different backgrounds.

Both these two directories contain two subdirectories, one called `images` contains the image files, the other called `labels` contains the VOC2007 format annotations.

- The `labels` of `Normal_Insulators` contains **only** the annotations of insulators;
- The `labels` of `Defective_Insulators` contains not only the annotations of insulators but also the annotations of defects which on the insulators.

The images is provided by the State Grid Corporation of China, and the dataset is made by WANG Zi-Hao.
If you have any question about this dataset, feel free to contact [zhwang0721@gmail.com](mailto:zhwang0721@gmail.com).
