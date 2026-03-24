# MRI-Data-Grapher
A simple script to graph snd analyze the Flow rate data obtained from an MRI from a patients left Ventricle.

## Language
- Matlab
## Features
- Plots a graph of Blood Pressure against the time it was recorded.
- Records each Peak and Trough
- Records each individual heart by dividing the data into seperate cardiac cycles
    - Plots an additional graph of each cardiac cycle overlapped on eachother
    - Estimates and stores the area under the graph of each cardiac cycle
    - Computes and displays the mean and standard deviation of the areas of all heartbeats.
 
## The Input

The provided file *flow.csv* contains measurements obtained from magnetic resonance imaging (MRI) of blood flow out of the patient's left ventricle. The goal is to visualize tha data to analyse how a heart responds to increased load experienced during exercise. The file containes two mcolumns of data, the patients blood pressure and the times' they had been recorded.

## The Process
To begin the file is opened with the ‘readmatrix’ function. Two matrices 'time’ and ‘flow’ are initialized from the data by reading their respective columns. By using the ‘smooth’ function, the data from the 'flow' matrix  can be smoothed and the subsequent matrix is saved as the vaiable ‘smoothflow’.

To find the peaks of each cycle, a loop is coded to go through each index of 'time' and checks if the pressure values at that moment are greater than the values ahead and behind it, and it checks if the value of pressure at that moment is greater than 300mmhg. If these condistions respond as True, then the value, the index, and the time it occured are all recorded.

To find the troughs if each cycle, a loop is coded to go hrough each index of ‘peak’, and from each peak travelling backwards the loop checks for the moment the value stops descending and can no longer increase. At this moment the value, index and time it occurred are recorded. After recording these values, that iteration of the loop is stopped with the ‘break’ command, and the loop is repeated with the next peak

To plot the data, The ‘figure’ command is utilized to facilitate the effective use of subplots. The unsmoothed data is plotted, and the smooth data is plotted with asterisk to indicate the locations of the starting points of the heartbeats.

To divide the data into seperate cardiac cycles, A hold is placed before the loop, because multiple plots are required to overlap within theloop. The loop runs throughout the length of ‘Trough’, and while using the ‘try’ and ‘catch’ command, the loop extracts a segment in ‘smoothflow’ from the current trough to the next, up until the next trough is invalid/non-existent in which the loop will ‘catch’ itself before an error and break.

Each segment is plotted on top of each other, on the same graph. The area under each plot is recorded using the ‘trapz’ and saved in the variable ‘area’. Afterwards, the title and label are written into code, and the hold is taken off.

To plot the histogram, one must simply use the histogram function , input their array and the amount of bars they desire. The mean and standard deviation are found using the respective commands, and the results are displayed to the user.

## The output

<img width="541" height="428" alt="image" src="https://github.com/user-attachments/assets/279127e8-98c4-4cc9-a669-d25d29176022" />

The analysis showed that the flow data during exercise followed a regular pattern.

The original flow data can be used to draw precise conclusions of the patients overall heartbeat, while the smoothed data can be displayed for visual convenience. Furthermore, displaying each cardiac cycle on the same graph could highlight any abnormalcies between the cycles, and visually demonstrate the magnitude by which the cycles may vary. The mean, standard deviation and area under the graph can provide a more mathematical analysis of the patients heart rate.

## What I learned

The purpose of this project was to deepen my understanding of commonly used commands and loops. 

### The For Loop:
-  Creating the 'for' loop to find the peaks taught me how to extrapolate numerous and various types of data within a single loop.
-  Additionally, creating the loop to find troughs I had to think outside the box and learned to extrapolate data using already established data.

### The 'hold' on and 'hold' off commands:
-  I had to learn how to properly use the hold function in order to plot multiple lines on the same graph. Understanding this function will take my ability to code graphical display's to the next level.

### The 'Try' and 'Catch' commands:
-  For this project, I learned to briefly use the try and catch command inside a loop. It is clear to me how much potential this command has in building stable and effective code and I'm eager to experiment with it more.

### Use in the medical field:
-  Overall, this project demonstrated how coding and data processing can be applied in the medical field to better understand heart function and detect potential health issues.

### Overall Growth:
Each part of this project helped me understand more about coding in Matlab, managing information, and improving patient experience. It was more than just making a tool, it was about solving problems, learning new things, and improving my skills for future projects and work.

## How It Can Be Improved
- Add a way to zoom in on the graphs, so that more precise information can be visually determined.
- Add a graphic display to present the mean and standard deviation in a clearer and visually better manner.
- Add a way to see individual cardiac cycles and their relevant information.
- Add a way to select and display graphical information from a specific timeframe.

## License
-  This project was completed for academic purposes and is open for educational use.

