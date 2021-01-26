https://img.shields.io/badge/Python-3.6.9-blue.svg
### <p align="center">AoI in Depth Prediction</p>  
This is a simplified version of struct2depth in pytorch.  
```
handle_motion  False
architecture    simple
joint_encoder  False
depth_normalization  True
compute_minimum_loss  True

Comment: There is no motion obejects prediction in this model!
```
![gif](./misc/rst.gif)  

The gif above is the training result of 1634 pictures and 95 epoches. 
<br> 
If you want to change the dataset size, you can change the length of the videos which are used for traning.<br> 
If YOU want to change the training epoches, you can change the line 160 in <i>main.py</i>
``` 
args_epochs = 100
``` 

heavily borrow code from [simplified_struct2depth](https://github.com/necroen/simplified_struct2depth), [sfmlearner](https://github.com/ClementPinard/SfmLearner-Pytorch) and [monodepth](https://github.com/ClubAI/MonoDepth-PyTorch).  
[original code in tensorflow](https://github.com/tensorflow/models/tree/master/research/struct2depth)  
<br>
**Environment**  
Google_Colab + python 3.6.9 + pytorch 1.0 + cuda 9.0 + opencv-python 4.1.2 + SciPy 1.1
<br>  
**Instruction**  

1. Film 2 videos which are 5-10 minutes using a smartphone without any moving objects, named the video as 1.mp4 and 2.mp4 and save them in the folder <i>video</i> <br />
2. Print the image <i>calib_jpg/Calib_Image_Print.png</i>. Then take several photos of the chessboard image from differet viewpoint (Front, upper, lower, left and righ).  <br />
4. Save all the image of the chessboard into the folder <i>calib_jpg</i>  <br />
5. Open the file Depth <i>Prediction.ipynb</i> using Google Colab. <br />
6. Upload the depth prediction code into Google drive. <br />
7. Mount your Google drive on your Google Colab <br />
8. Come into the depth prediction project folder <br />
```
cd drive/My Drive/Colab_Notebooks/Age_of_Information_in_Depth_Prediction 
``` 
9. Update required packages sSciPy 1.1 <br />
```
pip install scipy==1.1.0    
``` 
10. Run file <i>calib.py</i> <br />
```
!python calib.py 
``` 
11. Get camera intrinsics and copy the parameter matrix to <i>data_loader.py</i> line 129. <br />
12. run <i>main.py</i> to train the model by.<br />
``` 
!python main.py
``` 
13. Run the next inference cell for depth inference of a single RGB image.<br />
14. Because Google Colab's maximum lifetime is only 12 hours, but our project can run more than 24 hours. I set a pattern that let the model can learn from AoI breakpoint in the <i>main.py</i> line 383. You can restart the model training from the AoI value in the previous training if Google Colab terminates the previous training. To be mentioned, you should comment line 381 in the <i>main.py</i> if you restart the breakpoint training.<br />
15. The validation loss, training loss and AoI in seconds are saved in loss_new.txt.<br />
16. The MATALB code which plot AoI vs training loss and validation loss figures is in <i>MATLAB/Loss_Depth.m</i>.




