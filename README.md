# Semantic Segmentation

## Project Description
This project is labeling the pixels of a road in images using a Fully Convolutional Network (FCN).

### Training Dataset
For network training was used [Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php) from [here](http://www.cvlibs.net/download.php?file=data_road.zip) as suggested.

### Fully Convolutional Network implementation

As requested, all needed function were implemented (`load_vgg`, `layers`, `optimize` and `train_nn`).
As described in Lesson in `layers` was implemented FCN Encoder with convolutions and Decoder with upsampling to original image size and skip connections.

### Training Network
FCN was trained using described above Training Dataset with 50 epochs and using batch size = 5.
The latest output of loss functions:
```
Epoch: 50, Batch: 44, Loss: 0.027
Epoch: 50, Batch: 45, Loss: 0.026
Epoch: 50, Batch: 46, Loss: 0.022
Epoch: 50, Batch: 47, Loss: 0.018
Epoch: 50, Batch: 48, Loss: 0.030
Epoch: 50, Batch: 49, Loss: 0.023
Epoch: 50, Batch: 50, Loss: 0.029
Epoch: 50, Batch: 51, Loss: 0.031
Epoch: 50, Batch: 52, Loss: 0.029
Epoch: 50, Batch: 53, Loss: 0.031
Epoch: 50, Batch: 54, Loss: 0.026
Epoch: 50, Batch: 55, Loss: 0.028
Epoch: 50, Batch: 56, Loss: 0.021
Epoch: 50, Batch: 57, Loss: 0.024
```

### Results
The labeling results are quite good (fit to the rubric requirement of at least 80% road surface labeled), here are some pictures:
![Result1](runs/1517606483.1430795/umm_000040.png)
![Result2](runs/1517606483.1430795/um_000003.png)
![Result3](runs/1517606483.1430795/um_000027.png)
![Result4](runs/1517606483.1430795/um_000032.png)


## Project Description from original

### Introduction
In this project, you'll label the pixels of a road in images using a Fully Convolutional Network (FCN).

### Setup
##### Frameworks and Packages
Make sure you have the following is installed:
 - [Python 3](https://www.python.org/)
 - [TensorFlow](https://www.tensorflow.org/)
 - [NumPy](http://www.numpy.org/)
 - [SciPy](https://www.scipy.org/)
##### Dataset
Download the [Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php) from [here](http://www.cvlibs.net/download.php?file=data_road.zip).  Extract the dataset in the `data` folder.  This will create the folder `data_road` with all the training a test images.

### Start
##### Implement
Implement the code in the `main.py` module indicated by the "TODO" comments.
The comments indicated with "OPTIONAL" tag are not required to complete.
##### Run
Run the following command to run the project:
```
python main.py
```
**Note** If running this in Jupyter Notebook system messages, such as those regarding test status, may appear in the terminal rather than the notebook.

### Submission
1. Ensure you've passed all the unit tests.
2. Ensure you pass all points on [the rubric](https://review.udacity.com/#!/rubrics/989/view).
3. Submit the following in a zip file.
 - `helper.py`
 - `main.py`
 - `project_tests.py`
 - Newest inference images from `runs` folder  (**all images from the most recent run**)
 
 ### Tips
- The link for the frozen `VGG16` model is hardcoded into `helper.py`.  The model can be found [here](https://s3-us-west-1.amazonaws.com/udacity-selfdrivingcar/vgg.zip)
- The model is not vanilla `VGG16`, but a fully convolutional version, which already contains the 1x1 convolutions to replace the fully connected layers. Please see this [forum post](https://discussions.udacity.com/t/here-is-some-advice-and-clarifications-about-the-semantic-segmentation-project/403100/8?u=subodh.malgonde) for more information.  A summary of additional points, follow. 
- The original FCN-8s was trained in stages. The authors later uploaded a version that was trained all at once to their GitHub repo.  The version in the GitHub repo has one important difference: The outputs of pooling layers 3 and 4 are scaled before they are fed into the 1x1 convolutions.  As a result, some students have found that the model learns much better with the scaling layers included. The model may not converge substantially faster, but may reach a higher IoU and accuracy. 
- When adding l2-regularization, setting a regularizer in the arguments of the `tf.layers` is not enough. Regularization loss terms must be manually added to your loss function. otherwise regularization is not implemented.
 
### Using GitHub and Creating Effective READMEs
If you are unfamiliar with GitHub , Udacity has a brief [GitHub tutorial](http://blog.udacity.com/2015/06/a-beginners-git-github-tutorial.html) to get you started. Udacity also provides a more detailed free [course on git and GitHub](https://www.udacity.com/course/how-to-use-git-and-github--ud775).

To learn about REAMDE files and Markdown, Udacity provides a free [course on READMEs](https://www.udacity.com/courses/ud777), as well. 

GitHub also provides a [tutorial](https://guides.github.com/features/mastering-markdown/) about creating Markdown files.
