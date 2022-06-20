# E.coli segmentation

## Background
This research trained models for E.coli segmentation to improve the performance metrics including IoU (Intersection and Union), true positive, and f1 score.

Using our own training dataset, we train the segmentation model and test the performance on rod-shaped bacterial E.coli

## Steps
1. Preparation for starting: show gpu and memory information, pip install
2. Mask -> Flow: manual annotation -> simulated diffusion -> spatial gradients -> flow representations -> flow legend
3. Original Image -> SIM: original image -> eigenvalues of the Hessian -> shape index map
4. New Config of MiSiC: adjust the network structure, output from (256, 256, 1) -> (256, 256, 3)
5. Cellpose original Code: load cellpose.dynamics, cellpose.plot, cellpose.transforms
6. Mask -> Flow: all the training images from mask to flow field
7. Load new model: load the new defined model from step 4
8. Prepare dataset for training
- Input and ouput: x is Shape_Index-Map and output is Flow Field
- Image augmentations, image cropping and stitching, image rescale and noise addition
9. Train the model: train the model and save the network structure and parameters in hdf5 file
10. MiSiC Functions: load MiSiC functions of image postprocessing
11. Prediction: predict the masks based on the model trained

## Version
Segmentation_Cellpose is based on the Cellpose[1]

Segmentation_MiSiC is based on MiSiC[2]

Segmentation_Cellpose_MiSiC is the combination of [1] and [2]

## Reference
[1] Stringer, Carsen, et al. "Cellpose: a generalist algorithm for cellular segmentation." Nature methods 18.1 (2021): 100-106.

[2] Panigrahi, Swapnesh, et al. "Misic, a general deep learning-based method for the high-throughput cell segmentation of complex bacterial communities." Elife 10 (2021): e65151.
