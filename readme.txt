CONTENTS OF THIS FILE
---------------------

 * Introduction
 * Requirements
 * Contents
 * Setup/Installation
 * How to use
 * Output

---------------------
INTRODUCTION
 roiSelection is a Matlab graphics user interface (GUI) developed by Catalin D. Ciubotaru to automatically select cell boundaries.
 By clicking onto one well defined cell, the program will create a region of interest (ROI) around its boundaries.
 This program was used to analyze experimental in vivo data from Donati et al. http://researchdata.cab.unipd.it/547/.

--------------------- 
REQUIREMENTS
 MATLAB version: 2015a
 Input image format: .tif

--------------------- 
CONTENTS
 - ROISELECTION.zip containing:
 	- roiSelection.m
 	- roiSelection.fig
 - Figure_example.tif: example figure from which ROIs boundaries can be extracted. WARNING:Cell boundaries must be well defined for an efficient automatic ROI selection.
 - ROIs_example.mat: example output file of roiSelection
 - Figure_example_with ROIs.tif: example figure of the GUI. The ROIs in 'ROIs_example.mat' file are shown in blue.

--------------------- 
SETUP/INSTALLATION
 1. Download ROISELECTION folder
 2. Unzip the folder 
 2. Open Matlab
 3. Add the ROISELECTION folder to MATLAB path:
	Home -> Set Path -> Add Folder -> Selcet ROISELECTION folder -> Save -> Close
 4. To run the program, write in the command line: roiSelection
 5. A roiSelection GUI window will open
---------------------
HOW TO USE
 Click the button: Load Image
 Select the image from which you want to extact the ROIs: Figure_example.tif
 Click on the center of the cell you want to select; a ROI containing the selected cell will automatically appear (see Figure_example_with_ROIs.tif).
 Multiple ROIs can be selected by clicking on different cells.
 Consecutive numbers corresponding to consecutive ROIs will appear inside the 'Rois' panel after each selection.
 To better visualize cell boundaries, you can modify (sliding bars, from left to right): contrast, brightness and gamma filter.
 You can modify ROI selection parameters by changing 'Segment threshold' and 'ROI max size' (in pixels).
 You can delete a ROI by clicking on the corresponding number in the Rois panel and then on 'Delete roi' button.

 After having selected all the desired cells, click on the button 'Export rois' and save the .mat file (example 'ROIs_example.mat').
 WARNING: Export the selected ROIs only once you are sure to have selected all of them. You can not load and modify the ROI file once you have exported it.

---------------------
OUTPUT
 The program output is a .mat file (see 'ROIs_example.mat') structured as follows:
 - ROI: cell array; each cell corresponds to a ROI selected during the selection process.
 - Each cell is a structure containing:
	- Coordinates: matrix of the coordinates of the vectors of the polygon corresponding to the ROI;
	- Map: returns a segmented image BW, which is computed using the Fast Marching Method. The array specifies weights for each pixel. For documentation, see Matlab Help 'imsegfmm'.
	- SourcePoint: coordinates of the point you clicked to generate the ROI;
	- RoiMaxSize: maximum dimension of the ROI (imposed in the 'ROI max size' box).
	- hline: Control primitive line appearance and behavior. For documentation, see Matlab Help 'Primitive Line Properties'.
	- Rectangular: 0 (default value).






