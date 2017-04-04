# Usage
We assume that the convert*.m files as well as the lib/ directory are placed
on the same level as the data. 
i.e. the folder containing convert*.m and lib/ also contains the folders 
additional/, stratified/, test/, and training/.
You can run 

>>convertAll.m 

to generate a LF.mat file for each of the scenes.

If you have only downloaded a subset of the dataset you can generate the 
LF.mat files using 

>>convertBlenderTo5D('FOLDER').

The LF.mat includes the light field data (LF.LF), the ground truth 
(LF.depth/disp_high/lowres), a mask as well as the centerview. 
All parameters used for generation are loaded from the parameters.cfg and 
stored in LF.parameters.
If you are familiar with the H matrix from Donald Dansereaus "Decoding, 
Calibration and Rectification for Lenselet-Based Plenoptic Cameras" 
(http://www-personal.acfr.usyd.edu.au/ddan1654/PlenCal.pdf) the provide
the H matrix in LF.H. The distance between the two planes is stored in LF.f,
given in [mm].
Please note that this is not the focal length of the respective cameras,
which is stored in LF.parameters.intrinsics.focal_length_mm.

# Generating point clouds
To generate point clouds you can either run
>>[X,Y,Z] = getPointcloud(LF)

or

>>[X,Y,Z] = getPointcloud(LF,'disp',d)

Here, LF is the variable as generated by the conversion scripts, i.e. it
includes variables like LF, parameters and disp_lowres(:)]).
If you do not specify a disparity map d, it will visualize the ground truth.

# License
This work is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License. 
To view a copy of this license, visit http://creativecommons.org/licenses/by-nc-sa/4.0/. 
 
Authors: Katrin Honauer & Ole Johannsen 

Website: www.lightfield-analysis.net 

 
This add-on is based upon work of Maximilian Diebold. 

The 4D Light Field Benchmark was jointly created by the University of Konstanz and the HCI at Heidelberg University. If you use any part of the benchmark, please cite our paper "A dataset and evaluation methodology for depth estimation on 4D light fields". Thanks! 
 
 @inproceedings{honauer2016benchmark, 
 title={A dataset and evaluation methodology for depth estimation on 
 4D light fields}, 
 author={Honauer, Katrin and Johannsen, Ole and Kondermann, Daniel 
 and Goldluecke, Bastian}, 
 booktitle={Asian Conference on Computer Vision}, 
 year={2016}, 
 organization={Springer} 
 } 
