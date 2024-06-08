Vector Output Research README File 


Vector Output Research Code
Research at the Georgia Institute of Technology's 
Space Systems Design Lab with Professor Hirabayashi
Anay Naik 
April 2024


OUTPUT SUMMARY: 

This program script loads a .tab file using an inputted file, extracts specific columns and rows, and then generates a 3D vector output figure. This is based on data from vertex and tile vectors that are both in the file.


HOW TO USE THE PROGRAM PROJECT FILE:

1. Input the correct file name with its full file path as the variable filename. 

2. For the variable MV, input the correct rows and columns correlating to to the vertex vector points.
Example:  MV = MX(1 : 25350, 2 : 4);

3. For the variable MF, input the correct rows and columns correlating to to the tile vector points.
Example:  MF = MX(25351 : 25350 + 49152, 2 : 4);

4. Once the code is run, the program will then output a light based image based on the magnitude of the inputted vectors for vectors and tiles. 


PROGRAM DESCRIPTION: 

The user inputs the correct file name with with the full file path and set that to the variable filename. The filename is the implemented into the code using the load function. The next step is defining what rows and columns correlate to the vertex vector points in the loaded file which is defined as the variable MV. The next step is defining what rows and columns correlate to the vertex vector points in the loaded file which is defined as the variable MF. Then, defining what rows and columns correlate to the tile vector points in the loaded file which is defined as the variable MF. With these inputs, a figure is defined. That figure has its parameters set by the patch function using the faces and vertices that were defined earlier. The patch function creates "patches" of polygons that are defined by the coordinates of the vectors and tiles, which gives instructions on how the image should connect to each other. The final parameters make sure that the outputted figure is solely reliant on the light sources and then two light sources are specified.


SAMPLE PROBLEMS:

Example 1:

The following filename is loaded into the program:
filename =  'C:\Users\anayn\OneDrive\Desktop\Research Folder\originalinput.tab';

The file is loaded using the load function and defined as MX.

The vertex and tile columns and rows are defined respectively as MV and MF:
MV = MX(1 : 25350, 2 : 4);
MF = MX(25351 : 25350 + 49152, 2 : 4);

Using the patch function, the output is a figure that is based on two light sources and is defined by the coordinates for tiles and vectors. 

The figure is then outputted visually as the only output.


WRITTEN CODE: 

%%% Vector Output Research Code
%%% Research at the Georgia Institute of Technology's
%%% Space Systems Design Lab with Professor Hirabayashi
%%% Anay Naik April 2024


% Inputting Correct file name with the file path inputted.
filename =  'C:\Users\anayn\OneDrive\Desktop\Research Folder\originalinput.tab';
% Loading in the file using the Load lunction.
MX = load(filename);
% Defining the columns and rows that should be extracted from the tab file.
% The following values are for the vertex vector points.
% The values are hardcoded and must be changed for future differing input .tab files.
MV = MX(1 : 25350, 2 : 4);
% Defining the columns and rows that should be extracted from the tab file.
% The following values are for the tile vector points.
% The values are hardcoded and must be changed for future differing input .tab files.
MF = MX(25351 : 25350 + 49152, 2 : 4);
% Defining the outputted figure.
figure ()
% Defining outputted figure parameters.
set(gca , 'FontSize' , 18); hold on
% Patch function creates patches of polygons where coordinates
% and color can be defined for the outputted image.
patch('Faces' ,MF, 'Vertices' ,MV, 'FaceVertexCData' ,0.5*zeros(length(MV) , 1),...
    'FaceColor' , 'flat' , 'EdgeColor' , 'none');
% Keeps current plot so that new information can be added.
hold on
% Turns off axis lines.
axis off
% This makes the figure only reliant on the light source.
material dull
% Light source specified at [0,0,1000]
light ('Position' ,[0 0 1000] , 'Style' , 'local');
% Light source specified at [0,0,-4000]
light ('Position' ,[0 0 -4000],'Style' , 'local');