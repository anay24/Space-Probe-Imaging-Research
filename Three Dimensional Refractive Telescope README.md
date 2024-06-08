Three Dimensional Refractive Telescope Research README File 


Three Dimensional Refractive Telescope Research Code 
Research at the Georgia Institute of Technology's 
Space Systems Design Lab with Professor Hirabayashi
Anay Naik 
April 2024


OUTPUT SUMMARY: 

This program script asks the user for the following parameters: The aperture location x,y, and z coordinates, the aperture length and width, and the three triangular facet node vertex coordinates for the x, y and z axis. The output is an X matrix, Y matrix, and Z matrix for the corresponding coordinates based off of the inputted values.


HOW TO USE THE PROGRAM PROJECT FILE:

1. Before running the code, set the input variables. These input variables for the aperture are the x,y and z coordinates for the input variables as well as the pixel aperture length and width. The input variables for the triangular facet node includes the three vertex coordinates in the x, y, and z planes.  

2. Run the code. These input values will use plane and vector math for a three dimensional coordinate system to find the output coordinates. 

3. The final output will be three matrices, one for the X coordinate values one for the Y coordinate values, and one for the Z coordinate values.

PROGRAM DESCRIPTION: 

The user will input answers for the following data points: The aperture location x,y, and z coordinates, the aperture length and width, and the three triangular facet node vertex coordinates for the x, y and z axis. The purpose of the program is to simulate a three dimensional telescope with an aperture that is observing a plane. We can use the program to determine a vector intersection between each point on a predefined flat aperture plane, a focal point, and a randomly defined plane. The magnitude of the vector needs to be defined as the output in a X coordinate array, a Y coordinate array, and a Z coordinate array. The observed plane can be at any angle and it is in a triangular shape, meaning that all the points of the square aperture flat plane that do not hit the triangular plane need to output as NaN in value to show that there is no magnitude.
For the methodology on how the mathematics of the program works the following information will be useful. Determining the angle between the facet node plane and the aperture plane can be figured out by using the normal vector based on each plane. Doing this requires figuring out the normal vector of the flat plane which can be done by picking two points on the flat plane, creating two vectors by subtracting one point from the other twice, then doing the cross product of the two vectors. Then repeat the process for the user inputted points for the triangular facet. With the two normal vectors we can use an equation to get the angle between the two planes. The next step is to determine the location of every point and print their coordinate system. We can do this by creating two simultaneous for loops that vary for each possible combination of x and y coordinates since the plane is two dimensional in a three dimensional space. This is necessary for creating the magnitude outputs that are needed for the final solution. Using the amount of values specified by the length and width of the aperture, we can iterate through every coordinate that has been created using the two simultaneous for loops. For the idea of figuring out if the vector intersects with the triangular facet plane, we need to use parametric line equations for a three dimensional line. The equation requires one point on the line, the direction vector of the line, one point on the plane, and the normal vector for the plane. This equation gives us the ability to see where the vector crosses the facet plane. This gives us the parametric constant which can be used to be multiplied to each coordinate point that was created using the two simultaneous for loops and then added to the aperture location to get the output magnitude for every coordinate for each point. After calculating the magnitude of each coordinate point on the aperture we need to output the values into three different matrices, one for x, one for y, and one for z. However, since the output plane is a triangle, many of the vectors from the aperture may never reach the triangular facet. This is why it is necessary to make sure that a point is within the shape which is checked using the function inpolygon(). If the output is within the polygon, then the magnitude is displayed at the point. Otherwise, the output is displayed as NaN, meaning it did not reach the triangular facet. Then the output is shaped into the correct user inputted width and length and then displayed as three different matrices for each coordinate.  


SAMPLE PROBLEMS:

Example 1:

The following inputs are asked of the user: 

%% INPUT
%% Aperture Location Input Variables
% Enter x-coordinate of aperture location:
x_aperture = 5;
% Enter y-coordinate of aperture location:
y_aperture = 5;
% Enter z-coordinate of aperture location:
z_aperture = 5;

% What is the pixel aperture length?:
n_aperture = 5;
% What is the pixel aperture width?:
m_aperture = 5;

%% Triangular Facet Node 1 Input Variables
% Enter x-coordinate of node 1:
x1 = 0;
% Enter y-coordinate of node 1:
y1 = 0;
% Enter z-coordinate of node 1:
z1 = 2;

%% Triangular Facet Node 2 Input Variables
% Enter x-coordinate of node 2:
x2 = 3;
% Enter y-coordinate of node 2:
y2 = 3;
% Enter z-coordinate of node 2:
z2 = 8;

%% Triangular Facet Node 3 Input Variables
% Enter x-coordinate of node 3:
x3 = 4;
% Enter y-coordinate of node 3:
y3 = 1;
% Enter z-coordinate of node 3:
z3 = 3;

The output is written out in the command window as an X coordinate matrix, a Y coordinate matrix, and a Z coordinate matrix.

The output for this example is written as follows:

X Array:
       NaN       NaN       NaN       NaN       NaN
       NaN  -16.0000       NaN       NaN       NaN
       NaN    8.5000   19.0000       NaN       NaN
    6.5556    6.6154    6.7500    7.3333       NaN
       NaN       NaN       NaN       NaN    5.0000

Y Array:
       NaN       NaN       NaN       NaN       NaN
       NaN  -16.0000       NaN       NaN       NaN
       NaN    7.3333   19.0000       NaN       NaN
    5.3889    5.5385    5.8750    7.3333       NaN
       NaN       NaN       NaN       NaN    5.0000

Z Array:
       NaN       NaN       NaN       NaN       NaN
       NaN  -30.0000       NaN       NaN       NaN
       NaN   10.8333   40.0000       NaN       NaN
    6.9444    7.6923    9.3750   16.6667       NaN
       NaN       NaN       NaN       NaN   12.0000

CODE EXECUTION COMPLETE

Example 2:

The following inputs are asked of the user:  

%% INPUT
%% Aperture Location Input Variables
% Enter x-coordinate of aperture location:
x_aperture = 6;
% Enter y-coordinate of aperture location:
y_aperture = 6;
% Enter z-coordinate of aperture location:
z_aperture = 6;

% What is the pixel aperture length?:
n_aperture = 7;
% What is the pixel aperture width?:
m_aperture = 7;

%% Triangular Facet Node 1 Input Variables
% Enter x-coordinate of node 1:
x1 = 6;
% Enter y-coordinate of node 1:
y1 = 0;
% Enter z-coordinate of node 1:
z1 = 2;

%% Triangular Facet Node 2 Input Variables
% Enter x-coordinate of node 2:
x2 = 5;
% Enter y-coordinate of node 2:
y2 = 4;
% Enter z-coordinate of node 2:
z2 = 3;

%% Triangular Facet Node 3 Input Variables
% Enter x-coordinate of node 3:
x3 = 0;
% Enter y-coordinate of node 3:
y3 = 1;
% Enter z-coordinate of node 3:
z3 = 6;

The output is written out in the command window as an X coordinate matrix, a Y coordinate matrix, and a Z coordinate matrix.

The output for this example is written as follows:

X Array:
       NaN       NaN       NaN       NaN       NaN       NaN       NaN
    4.0233       NaN       NaN       NaN       NaN       NaN       NaN
    4.0460    4.3210       NaN       NaN       NaN       NaN       NaN
    4.0682    4.3415    4.6579    5.0286       NaN       NaN       NaN
    4.0899    4.3614    4.6753    5.0423    5.4769    6.0000       NaN
       NaN       NaN       NaN       NaN       NaN       NaN       NaN
       NaN       NaN       NaN       NaN       NaN       NaN       NaN

Y Array:
       NaN       NaN       NaN       NaN       NaN       NaN       NaN
    4.4186       NaN       NaN       NaN       NaN       NaN       NaN
    4.8276    4.7407       NaN       NaN       NaN       NaN       NaN
    5.2273    5.1707    5.1053    5.0286       NaN       NaN       NaN
    5.6180    5.5904    5.5584    5.5211    5.4769    5.4237       NaN
       NaN       NaN       NaN       NaN       NaN       NaN       NaN
       NaN       NaN       NaN       NaN       NaN       NaN       NaN

Z Array:
       NaN       NaN       NaN       NaN       NaN       NaN       NaN
    3.6279       NaN       NaN       NaN       NaN       NaN       NaN
    3.6552    3.4815       NaN       NaN       NaN       NaN       NaN
    3.6818    3.5122    3.3158    3.0857       NaN       NaN       NaN
    3.7079    3.5422    3.3506    3.1268    2.8615    2.5424       NaN
       NaN       NaN       NaN       NaN       NaN       NaN       NaN
       NaN       NaN       NaN       NaN       NaN       NaN       NaN

CODE EXECUTION COMPLETE


WRITTEN CODE: 

%%% Three Dimensional Refractive Telescope Research Code 
%%% Research at the Georgia Institute of Technology's 
%%% Space Systems Design Lab with Professor Hirabayashi
%%% Anay Naik April 2024

clear;
clc;
close all

%% INPUT
%% Aperture Location Input Variables
% Enter x-coordinate of aperture location:
x_aperture = 5;
% Enter y-coordinate of aperture location:
y_aperture = 5;
% Enter z-coordinate of aperture location:
z_aperture = 5;

% What is the pixel aperture length?:
n_aperture = 5;
% What is the pixel aperture width?:
m_aperture = 5;

%% Triangular Facet Node 1 Input Variables
% Enter x-coordinate of node 1:
x1 = 0;
% Enter y-coordinate of node 1:
y1 = 0;
% Enter z-coordinate of node 1:
z1 = 2;

%% Triangular Facet Node 2 Input Variables
% Enter x-coordinate of node 2:
x2 = 3;
% Enter y-coordinate of node 2:
y2 = 3;
% Enter z-coordinate of node 2:
z2 = 8;

%% Triangular Facet Node 3 Input Variables
% Enter x-coordinate of node 3:
x3 = 4;
% Enter y-coordinate of node 3:
y3 = 1;
% Enter z-coordinate of node 3:
z3 = 3;



%% OUTPUT
%% Angle between facet node plane and aperture location plane
% Three points on a flat plane at z = 0 for cross product
ap1 = [0,0,0];
ap2 = [1,1,0];
ap3 = [5,6,0];
apnormal = cross(ap1-ap2, ap1-ap3);
% Three points on the facet node plane for cross product
ap4 = [x1,y1,z1];
ap5 = [x2,y2,z2];
ap6 = [x3,y2,z3];
normal2 = cross(ap4-ap5, ap4-ap6);
% Finding angle between the two planes using their cross products and normal vectors
theta=acosd(abs(sum(apnormal.*normal2))/norm(apnormal)/norm(normal2));

%% Determining location for each point 
appoint = [x_aperture,y_aperture,z_aperture];
num = 1;
for i = 1:n_aperture
    for j = 1:m_aperture
        % Figuring out the every different data point at the same z height point 
        vect{num} = [x_aperture-i,y_aperture-j,z_aperture-0];
        num = num + 1;
    end
end

%% Determining value for each point
lengthvect = length(vect);
for k = 1:lengthvect

    % Plane offset parameter for parametric line
    d = -dot(normal2,ap4);
    % Creating the parametric line parameter for each vector point
    t = - (d + dot(normal2,appoint)) / dot(normal2,vect{k});
    % Intersection coordinate for each vector point
    Iout{k} = appoint + vect{k}*t;

end

%% Creating output matrix and removing values not in the facet node
xs = [x1,x2,x3];
ys = [y1,y2,y3];

for q = 1:(length(Iout))

    outval = Iout{q};
    vals = vect{q};
    vals1 = vals(1);
    vals2 = vals(2);
    % Testing if each point is within triangular facet node
    in = inpolygon(vals1,vals2,xs,ys);

    if in == true
        % If the point is within the triangular facet node, then output is
        % displayed
        xarrayoutput(q) = outval(1);
        yarrayoutput(q) = outval(2);
        zarrayoutput(q) = outval(3);
    else
        % If the point is not within the triangular facet node, then NaN is
        % displayed
        xarrayoutput(q) = NaN;
        yarrayoutput(q) = NaN;
        zarrayoutput(q) = NaN;
    end

end

% Reshaping output arrays into correct user inputted dimensions
xarrayoutput = reshape(xarrayoutput,n_aperture,m_aperture);
yarrayoutput = reshape(yarrayoutput,n_aperture,m_aperture);
zarrayoutput = reshape(zarrayoutput,n_aperture,m_aperture);

%% Printing Arrays
disp('X Array:')
disp(xarrayoutput)
disp('Y Array:')
disp(yarrayoutput)
disp('Z Array:')
disp(zarrayoutput)
disp('CODE EXECUTION COMPLETE');
