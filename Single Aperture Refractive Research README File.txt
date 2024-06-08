Single Aperture Refractive Telescope Research README File 


Single Aperture Refractive Telescope Research Code
Research at the Georgia Institute of Technology's 
Space Systems Design Lab with Professor Hirabayashi
Anay Naik 
April 2024


OUTPUT SUMMARY: 

This program script asks the user in a pop-up window for the following parameters: focal length in centimeters, height in centimeters, boresight or surface angle in degrees, and the input pixel count. The output is an X array and a Y array that correspond to the input values. 


HOW TO USE THE PROGRAM PROJECT FILE:

1. When the code is run, a pop-up window will present itself and ask for focal length in centimeters, height in centimeters, boresight to surface angle in degrees, and the input pixel count.

2. These inputs values will run through a couple equations for a single aperture refractive telescope in two dimension. 

3. The final output will be two arrays, one for the X coordinate values and one for the Y coordinate values. They will correspond with the pixel count which will correlate to the amount of input coordinates. 


PROGRAM DESCRIPTION: 

The user will input answers in a pop-up window for the following questions: 'What is the focal length in centimeters (f)?','What is the height in centimeters (h)?','What is the boresight to surface angle in degrees (theta)?','What is the input pixel count?'. These values will be used for equations that are based on a single aperture refractive telescopic system in two dimensions. The inputs go through error mitigation to make sure that they make sense for the equations and how the parameters are set up. With the user-inputted values, the program constructs an initial array that creates a number line with a zero at the center of the number line, making sure that the length correlates with the value inputted for pixel count. An example of this is that if if pixcount = 6 then xarray = [-3,-2,-1,1,2,3] where xarray is the initial array used for calculations. The initial array also varies based on whether the input is odd or even, so with an odd input for the pixel count, there will be a zero at the center of the array, and if it is an even input, then the code will not have a zero in the center of the array. Each value of the initial array will be inputted into a set of equations that will create two arrays, one for the final X values and one for the final Y values. The final X array values depend on the focal length and height where a vector from the initial array must hit the focal point and then hit the object plane. For the final Y array, the values are all the same as the focal length added to the height if the boresight to surface angle is zero. If the boresight to surface angle is not zero, then the final Y array varies in depth based on how large the angle is. The final X array and final Y array are outputted in the command window and the code execution is then complete. 


SAMPLE PROBLEMS:

Example 1:

The following inputs are asked of the user in a pop-up window with the questions: 

'What is the focal length in centimeters (f)?'
'What is the height in centimeters (h)?'
'What is the boresight to surface angle in degrees (theta)?'
'What is the input pixel count?'

The user answers with the following inputted numbers:

 f = 20;
 h = 100;
 theta = 0;
 pixcount = 24; 

The output is written out in the command window as with both an X array and a Y array.

The output is written as follows:

X Array:  -60  -55  -50  -45  -40  -35  -30  -25  -20  -15  -10  -5  5  10  15  20  25  30  35  40  45  50  55  60 
Y Array:  120  120  120  120  120  120  120  120  120  120  120  120  120  120  120  120  120  120  120  120  120  120  120  120 
CODE EXECUTION COMPLETE

Example 2: 

The following inputs are asked of the user in a pop-up window with the questions: 

'What is the focal length in centimeters (f)?'
'What is the height in centimeters (h)?'
'What is the boresight to surface angle in degrees (theta)?'
'What is the input pixel count?'

The user answers with the following inputted numbers:

 f = 24;
 h = 200;
 theta = 10;
 pixcount = 16; 

The output is written out in the command window as with both an X array and a Y array.

The output is written as follows:

X Array:  -67  -58  -50  -42  -33  -25  -17  -8  8  17  25  33  42  50  58  67 
Y Array:  181  186  192  197  202  208  213  219  229  235  240  246  251  256  262  267 
CODE EXECUTION COMPLETE


WRITTEN CODE: 

%%% Single Aperture Refractive Telescope Research Code
%%% Research at the Georgia Institute of Technology's
%%% Space Systems Design Lab with Professor Hirabayashi
%%% Anay Naik April 2024

clear; 
clc; 
close all

    %% INPUT VARIABLES
% A prompt shows up when the code is run for the user to directly input the
% focal length, height, angle, and pixel count.
    inputQuestions = {'What is the focal length in centimeters (f)?','What is the height in centimeters (h)?','What is the boresight to surface angle in degrees (theta)?','What is the input pixel count?'};
    inputTitle = 'Refractive Telescope Input Variables';
    inputSize = [1 65];
    inputPresets = {'20','100','0','1024'};
    inputAnswer = inputdlg(inputQuestions,inputTitle,inputSize,inputPresets);
    
    f = str2double(inputAnswer{1});
    h = str2double(inputAnswer{2});
    theta = str2double(inputAnswer{3});
    pixcount = str2double(inputAnswer{4}); 

%Error mitigation for inputs not being negative
if f < 0 || h < 0 || theta < 0 || h+f == 0
     promptMessaget = sprintf('INPUT ERROR\nInputs must be positive.');
        buttont = questdlg(promptMessaget, 'INPUT ERROR','Ok','Ok');
        if strcmp(buttont, 'Ok')
            return; 
        end 
end  
    %% BUILDING X ARRAY
% If the pixel count is even, then the code splits the pixel count in half
% and creates half negative and half positive numbers 
    %Example: if pixcount = 6 then xarray = [-3,-2,-1,1,2,3]
    if rem(pixcount,2) == 0 && pixcount > 1 && isreal(pixcount) && (rem(pixcount,1) == 0)
        split = pixcount/2;
        si = [-split:-1];
        sj = [1:split];
        xarray = [si sj];
% If the pixel count is odd, then the code splits the pixel count in half
% and creates half negative and half positive numbers and puts a zero in
% between
    %Example: if pixcount = 7 then xarray = [-3,-2,-1,1,2,3]
    elseif rem(pixcount,2) == 1 && pixcount > 1 && isreal(pixcount) && (rem(pixcount,1) == 0)
        splitcount = pixcount-1;
        split = splitcount/2;
        si = [-split:-1];
        sj = [1:split];
        xarray = [si 0 sj];
 % This is error mitigation for inputs 
 % if pixel count is neither odd or even, then the code cannot function
    else
       promptMessaget = sprintf('INPUT ERROR\nPixel count is not feasible.');
        buttont = questdlg(promptMessaget, 'INPUT ERROR','Ok','Ok');
        if strcmp(buttont, 'Ok')
            return; 
        end 
    end

   %% FORMULAS

   i = 1000*xarray; %ith pixel = d*i
   hfratio = (h/f);
   fhratio = (f/h);
   absfhratio = abs(fhratio);
   z = xarray*hfratio; %z = i*d*(h/f)
   l = z/cos(theta); %z = l*cos(theta)
   hprime = h + l*sin(theta); % hprime = h + l*sin(theta)
   diffh = l*sin(theta); 
   xarrayoutput = z;

    if theta == 0 %when there is no angle, the y array stays constant at h+f
        youtput = h + f; 
        yarrayoutput = youtput*ones(1,pixcount);
    else %when there is angle, the y array is hprime+f but hprime changes
        youtput = hprime + f;
        yarrayoutput = youtput;
    end
   

    %% PRINTING ARRAYS

    fprintf(['X Array: ' repmat(' %1.0f ',1,numel(xarrayoutput)) '\n'],xarrayoutput);
    fprintf(['Y Array: ' repmat(' %1.0f ',1,numel(yarrayoutput)) '\n'],yarrayoutput);
    disp('CODE EXECUTION COMPLETE');
