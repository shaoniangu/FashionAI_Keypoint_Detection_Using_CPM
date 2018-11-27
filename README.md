# FashionAI costume key point positioning global challenge *AILAB-ZJU* source code (continue to update latest experiment)
* Name of the competition: Tianchi FashionAI costume key point positioning global challenge
* Team Name: AILAB-ZJU
* Rank of the first season: 70/2322
* Rank of the second season: 41/2322
* Best result: NE = 4.45% for the second season

## To Do
* Modify FPN, I find there are some inproper setting of FPN.
* Add some new kinds of feature fusion strategy proposed in recent literatures.
* Rethink and deal with the key point positioning accuracy of the first stage which is the basis of the following stages.
* Add PAF to jointly assistant the key point positioning.
* Some other ideas.

## Results display
![blouse](https://github.com/shaoniangu/Realize_Convolutional_Pose_Machines_On_FashionAI/raw/master/Readme_images/blouse.jpg)
![dress](https://github.com/shaoniangu/Realize_Convolutional_Pose_Machines_On_FashionAI/raw/master/Readme_images/dress.jpg)
![outwear](https://github.com/shaoniangu/Realize_Convolutional_Pose_Machines_On_FashionAI/raw/master/Readme_images/outwear.jpg)
![skirt](https://github.com/shaoniangu/Realize_Convolutional_Pose_Machines_On_FashionAI/raw/master/Readme_images/skirt.jpg)
![trousers](https://github.com/shaoniangu/Realize_Convolutional_Pose_Machines_On_FashionAI/raw/master/Readme_images/trousers.jpg)

## Code Environment Description
Our code execution environment is:
* Operating System: Ubuntu16.04 LTS
* Python version: 3.5.1
* Opencv version: 3.3.0.10
* Tensorflow version: 1.3.0
* Required library functions: pickle, pandas, numpy, math, os, sys, matplotlib, random, time, skimage, scipy, PIL, importlib, configparser, imageio
* Baseline model used: Convolutional Pose Machines
* Baseline model original author copyright: Apache License 2.0
* Baseline model original author code address: https://github.com/timctho/convolutional-pose-machines-tensorflow
* Please follow the Apache License 2.0 rules，use only for shared learning.

## code structure description
The whole set of code files consists of three parts: Results, Train, and Test. Among them, Results is the folder for storing gt results and evaluation codes, Train is train code files, and Test is test code files. The structure is shown below.
```
|--Results
|--Train
   |--no occlusion
	 |--models
	 |--preprocess
	 |--config.py
	 |--run_training.py
   |--Other files of different experiments are similar
|--Test
   |--normal_test
	 |--checkpoints documents
	 |--models
	 |--preprocess
	 |--config.py
	 |--test_config.py
	 |--run_test.py
   |--test_add_aug
	 |--checkpoints documents
	 |--models
	 |--preprocess
	 |--config.py
	 |--test_config.py
	 |--run_test.py
   |--test_add_aug_with_IOU
	 |--checkpoints documents
	 |--models
	 |--preprocess
	 |--config.py
	 |--test_config.py
	 |--run_test.py
|--README.md
```
**Detailed description**:
* **Train**: Contains multiple experiment files. Each folder contains an experiment code, the file name is the experiment name. Each file consists of four parts: *models*, *preprocess*, *config.py*, and *run_training*, where *models* is the model file and *preprocess* is the data generator file. The file *config.py* is the training configuration file, and *run_training* is the training execution file. Experiment *no occlusion* means that we don't take the unvisible keypoint into consideration when training for the Evaluation index NE just calculate the accuracy of visible keypoints. Experiment *add occlusion* means that we take the unvisible keypoint into consideration when training. Experiment with 'fpn' means we fuse basic cpm model with the idea of Feature Pyramid Network.
* **Test**: Contains three kinds of test modes: regular test, test with augmented test, and test considering the area ratio of the clothes, whose file names are *normal_test*, *test_add_aug* and *test_add_aug_with_IOU*. The test files are composed of six parts: *checkpoints*, *models*, *preprocess*, *config.py*, *test_config.py*, and *run_test*. Among them, "checkpoints" stores the parameters of the model generated by the training. The checkpoint folder needs to be generated and copied from Train. Models is the model file. Preprocess stores py files for test image preprocessing. *config.py* is a training configuration file., *test_config.py* is the test configuration file, *run_test.py* is the test execution file.

## Train procedure
* Modify the two paths in *preprocess/config.cfg* in each experiment file. The paths to be modified are ```train_data_file``` and ```img_directory```, which are the paths of csv files for train labels and training images.
* Configure the training parameters in *config.py*.
* Modify some of the code in the *run_training.py* to save the path, customize your own path structure.
* Extra attention: For some reasons, we can't disclose the learning rate we use. Other learning rates, such as attenuation learning rate, can be improved in the model file to be called to improve the learning rate in build_loss2(), build_loss3(), build_loss4(). , or open the comment directly in run_training.py, using build_loss().
* Run *run_training.py* to train the model. The checkpoints generated by each model run will be saved in a newly generated file.

## Test procedure
* Please copy the files generated by the training with checkpoints to the Test folder.
* Also need to modify the path, one is /preprocess/test_preprocess_config.py, one is * Valid_config.py *, two file path you want to modify are `` `test_img_directory``` and` `` test_data_file``` , which are the folder path of the test images and the path of the csv file for test image labels.
* Run the test file /preprocess/test_preprocess.py, pre-processing test data, the size of the test image center padding to the network input.
*  Moreover, you should modify preprocessed image path address and checkpoint files address in * Valid_config.py *.
* If you want, you can also modify some of the path to save in *run_test.py*, customize your own path structure.
* run * Run_test.py *  to test. After test, there will be a new csv file, which is the csv file of predicted labels.


# FashionAI服饰关键点定位全球挑战赛 *AILAB-ZJU* 源码（持续更新最新实验）
* 比赛名称：天池FashionAI服饰关键点定位全球挑战赛
* 队伍名称：AILAB-ZJU
* 第一赛季排名：70/2322
* 第二赛季排名：41/2322
* 最好成绩：第二赛季B榜NE=4.45%

## 计划实验
* 修改FPN，我发现FPN的设置有一些问题。
* 增加近年来文献中提出的几种新的特征融合策略。
* 重新思考和解决第一阶段的关键点定位精度问题，这是后续阶段的基础。
* 添加PAF策略辅助关键点定位。
* 其他一些想法。

## 结果展示
![blouse](https://github.com/shaoniangu/Realize_Convolutional_Pose_Machines_On_FashionAI/raw/master/Readme_images/blouse.jpg)
![dress](https://github.com/shaoniangu/Realize_Convolutional_Pose_Machines_On_FashionAI/raw/master/Readme_images/dress.jpg)
![outwear](https://github.com/shaoniangu/Realize_Convolutional_Pose_Machines_On_FashionAI/raw/master/Readme_images/outwear.jpg)
![skirt](https://github.com/shaoniangu/Realize_Convolutional_Pose_Machines_On_FashionAI/raw/master/Readme_images/skirt.jpg)
![trousers](https://github.com/shaoniangu/Realize_Convolutional_Pose_Machines_On_FashionAI/raw/master/Readme_images/trousers.jpg)

## 代码环境说明
我们的代码运行环境为：
* 操作系统：Ubuntu16.04 LTS
* Python版本：3.5.1
* Opencv版本：3.3.0.10
* Tensorflow版本：1.3.0
* 必要的库函数：pickle、pandas、numpy、math、os、sys、matplotlib、random、time、skimage、scipy、
* PIL、importlib、configparser、imageio
* 使用的Baseline模型：Convolutional Pose Machines
* Baseline模型原作者版权：Apache License 2.0
* Baseline模型原作者代码地址：https://github.com/timctho/convolutional-pose-machines-tensorflow
* 使用时请遵循Apache License 2.0规定，在此仅供分享学习。

## 代码结构说明
整套代码文件由Results、Train、Test三部分构成，其中Results为存放gt结果和评测代码的文件夹、Train为训练代码文件、Test为测试代码文件，结构展示如下：
```
|--Results
|--Train
   |--no occlusion
	 |--models
	 |--preprocess
	 |--config.py
	 |--run_training.py
   |--其它实验文件类同
|--Test
   |--normal_test
	 |--checkpoints documents
	 |--models
	 |--preprocess
	 |--config.py
	 |--test_config.py
	 |--run_test.py
   |--test_add_aug
	 |--checkpoints documents
	 |--models
	 |--preprocess
	 |--config.py
	 |--test_config.py
	 |--run_test.py
   |--test_add_aug_with_IOU
	 |--checkpoints documents
	 |--models
	 |--preprocess
	 |--config.py
	 |--test_config.py
	 |--run_test.py
|--README.md

```
**详细说明**：
* **Train**：包括多个实验文件，每个文件夹包含一种实验代码，文件名即实验名称。每个文件均由*models*、*preprocess*、*config.py*和*run_training*四个部分构成，其中*models*中存放的是模型文件，*preprocess*中存放的是数据生成器的py文件，*config.py*是训练的配置文件，*run_training*为训练的执行文件。
* **Test**：包含三种test模式，分别是常规test、带增广的test、结合衣服面积占比增广的test，文件名称分别为*normal_test*、*test_add_aug*、*test_add_aug_with_IOU*。测试文件均由*checkpoints*、*models*、*preprocess*、*config.py*、*test_config.py*和*run_test*六个部分构成，其中“checkpoints”中存放的是训练生成的模型参数的checkpoint文件夹，需从Train中生成并拷贝过来，models中存放的是模型文件，preprocess中存放的是测试图片预处理的py文件，*config.py*是训练的配置文件（测试时需要搭建训练时的模型结构），*test_config.py*是测试的配置文件，*run_test.py*为测试的执行文件。

## 训练流程
* 修改每个实验文件中的*preprocess/config.cfg*中的两个路径，要修改的路径为```train_data_file```和```img_directory```，分别为训练图片的标签csv文件路径和训练图片路径。
* 配置*config.py*中的训练参数。
* 修改*run_training.py*中一些关于路径保存的代码，自定义自己的路径结构。
* 格外注意：因为一些原因暂不能公开我们用的学习率，其他学习率例如衰减学习率均可，请在要调用的模型文件中完善build_loss2()、build_loss3()、build_loss4()中的学习率，或在run_training.py中直接打开注释，使用build_loss()。
* 运行*run_training.py*训练模型，每个模型运行生成的checkpoint将会保存在新生成包含有checkpoints的文件。

## 测试流程
* 请将训练生成的保存有checkpoint的文件拷贝至Test中文件夹下。
* 同样需要修改路径，一处为/preprocess/test_preprocess_config.py，一处为*Valid_config.py*，两个文件中要修改的路径均是```test_img_directory```和```test_data_file```，分别为测试图片的文件夹路径和测试图片标签csv文件的路径。
* 运行测试文件中的/preprocess/test_preprocess.py，进行测试数据的预处理，将测试图片中心padding到网络输入的大小。
* 此外还要修改*Valid_config.py*中预处理好的图片路径地址以及checkpoint文件地址。
* 修改*run_test.py*中一些关于路径保存的代码，自定义自己的路径结构。
* 运行*run_test.py*进行测试,测试后会生成一个新的csv的文件，此文件中保存的便是预测的标签。