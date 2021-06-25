# Fake Video Detection

<img src="banner.png" align="middle" width="3000"/>

Hello! Here is my personal submission for an object detection task for Brainhack's [SeeTrue Workshop](https://www.dsta.gov.sg/brainhack) hackathon.

My implementation makes use of Faster R-CNN model with a ResNet50-FPN backbone. To understand the underlying code structure, you can read this [article](https://zhuanlan.zhihu.com/p/145842317) by translating to English.

Through robust augmentations and hyperparameter tuning, I was able to achieve an average log loss of 0.3225 on unseen photos.

# Use my implementation

### Downloading my Source Code
- Visit the [repository](https://github.com/raythx98/Object-Detection)
- Click on `Objection Detection.ipynb`
- Click on the download button

### Upload the Jupyter Notebook
- Upload the Jupyter Notebook to your google drive
- Note: `/content/drive/MyDrive` is your google drive home directory
- Open the Jupyter Notebook
- Change your runtime by following these steps
    1. Click on `runtime`
    2. Click on `change runtime type`
    3. Change hardware accelerator to `GPU`

### Configure the Notebook
- Open the Jupyter Notebook
- Under `Importing dataset from Google Drive`, change `base_folder` to your desired path
- rename the zip file for `training_path` and `testing_path`, more on creating your dataset [below](#creating-your-datasets)

### Creating your datasets

#### Dataset format
Your datasets `training_dataset.zip` and `test_dataset.zip` should follow the following format:

```
dataset.zip/
  dataset/
    train/
      fake_image/
      .  00001/
      .  .  frame00001.jpg
      .  .  frame10001.jpg
      .  .  frame20001.jpg
      .  .  ...
      .  00002/
      .  .  frame00001.jpg
      .  .  frame10001.jpg
      .  .  frame20001.jpg
      .  .  ...
      .  00003/
      .  .  frame00001.jpg
      .  .  frame10001.jpg
      .  .  frame20001.jpg
      .  .  ...
      .  ...
      real_image/
      image_labels.csv
    val/
      fake_image/
      real_image/
      image_labels.csv
```

#### Format for training and validation json files
`train.json` and `val.json` should follow the following format:

> Note that this is different from `test.json` [below](#format-for-test-json-file).
> 
> For `train.json` and `val.json`, we will require image width and height to be specified under `images`. Also, `annotations` are not needed for `test.json`
> 
`image_labels.csv` is structured as follows
```
filename                        | class
fake_image/00000/frame00001.jpg | fake
fake_image/00000/frame10001.jpg | fake
fake_image/00000/frame20001.jpg | fake
...
```

#### Format for test json file

`test.json` should follow the following format:

```
train.json/
    {
    .   "categories": [
    .   .   {
    .   .       "id": 1,
    .   .       "name": "Cat",
    .   .   },
    .   .   {
    .   .       "id": 2,
    .   .       "name": "Dog",
    .   .   },
    .   .   ...
    .   ],
    .   
    .   "images": [
    .   .   {
    .   .       "id": 1,
    .   .       "file_name": "00001.jpg",
    .   .   },
    .   .   {
    .   .       "id": 2,
    .   .       "file_name": "00002.jpg",
    .   .   },
    .   .   ...
    .   ]
    }
```

### Final Steps

1. Save the changes you have made till now

2. Upload `training_dataset.zip` and `test_dataset.zip` into `base_folder`

3. Click on `Runtime` then `Run All`
