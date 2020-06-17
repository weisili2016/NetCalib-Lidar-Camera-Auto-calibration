## NetCalib: A Novel Approach for LiDAR-Camera Auto-calibration Based on Deep Learning

This work is published as a paper in icpr 2020.

<img src="assets/Auto-Calibration-Figure.png" width="1600" alt="Train_Accuracy">

In this paper, we demonstrated a novel approach to calibrate the LiDAR and Stereo cameras using a deep neural network.
Firstly, LiDAR point cloud is projected to the depth map in the left camera's view, and the depth map for the corresponding stereo pair is calculated as well.
Next, two modality-specific feature extraction modules are used for two depth maps respectively to preprocess and extract features from each modality.
Then, the output feature maps are concatenated and they are fed to the global regression module that will learn the geometry correspondencies among modalities. 
A SPP layer is used after the output from previous module to provide a fixed length feature vector.
Finally, two sets of output layers are used for rotation errors and translation errors separately.

### Experiment results
#### 1. Losses
<img src="assets/train_loss.png" width="300" alt="train-loss"> <img src="assets/valid_loss.png" width="300" alt="valid-loss"> <img src="assets/test_loss2.png" width="300" alt="valid-loss">

#### 2. Model inference error
<img src="assets/error-rotation.png" width="400" alt="rotation-error"> <img src="assets/error-translation.png" width="400" alt="translation-error">

#### 3. Visualization
| | Sample 1 | Sample 2 |
| :---:  | :---: | :---: |
| LiDAR with error | <img src="assets/test-1-lidar-err.png" width="700" alt="lidar-err-1"> | <img src="assets/test-193-lidar-err.png" width="700" alt="lidar-err-2">|
| LiDAR fixed | <img src="assets/test-1-lidar-fix.png" width="700" alt="lidar-fix-1"> | <img src="assets/test-193-lidar-fix.png" width="700" alt="lidar-fix-2">
| LiDAR ground truth | <img src="assets/test-1-lidar-gt.png" width="700" alt="lidar-gt-1"> | <img src="assets/test-193-lidar-gt.png" width="700" alt="lidar-gt-2">
| Stereo depth | <img src="assets/test-1-stereo.png" width="700" alt="lidar-stereo-1"> | <img src="assets/test-193-stereo.png" width="700" alt="lidar-stereo-2">

### Deployment
The codes were tested on Ubuntu 19.10 & 20.04 with Python 3.7 & 3.8. Generally, a Ubuntu 18.04+ with Python3+ will be compatible as long as you can install those required libraries.

1. Clone the repo to your local drive. 
2. Setup your own Python environment and install the `requirements.txt` by command `pip3 install -r requirements.txt`. 

### Train the model
Modify the configurations in `src/config.py`. 
You can start training the model from the beginning using `--train` argument. 
`--err` specifies the error range to use, which is defined in the configuration.

```shell script
python main.py --train --err 3
```

In order to continue training, you can add `--ckpt` argument to specify the pytorch checkpoint `tar` file.

### Test the model
You can test the trained model by the command below, where `--win-scale` changes the opencv window size.

```shell script
python main.py --test --err 4 --ckpt /home/user/NetCalib-Lidar-Camera-Auto-calibration/results/test1/ckpt/ckpt.tar --win-scale 2.5
```
### Licence 
NetCalib is released under a [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) license. For a list of all ...... dependencies, please see .......

For a closed-source version of NetCalib for commercial purposes, please contact the authors: its.


### Contributors
Shan Wu 
Amnir Hadachi 
Damien Vivet 
Yadu Prahbakar

### Citation 
If you use NetCalib in an academic work, please cite:


Preprint version of the paper is here.

### References
