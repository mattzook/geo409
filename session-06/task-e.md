#Task E: JavaScript Functions

**Instructions:** First, copy over the directory [https://github.com/newmapsplus/geo409/session-06/task/](https://github.com/newmapsplus/geo409/session-06/task/) into the root directory of your personal *geo409* Git repository and rename it to `task-e` -- just like you previously did with tasks a to d. Modify the *index.html* within this directory to fulfill the requirements listed below. 

The goal of this task is to create 3 functions: 1) prepares 4 Array data structures and pass these Array variables as arugments to a second function that, 2) accepts the 4 variables as parameters and uses a looping structure to populate the map with markers with the data, and 3) calculates the population density of each city, returning this value to the 2nd function to be used within a popup message. 

Save your changes to your *index.html* file and **commit changes to your local GitHub repository** as you work. Begin your coding beneath line 85 containing the comment `begin writing/editing Task E code here`. The instructions below will guide you through this process. Note that, beyond the instructions below, the comments within the script also inform you of where and what you should be coding.

To begin, first open the task/index.html file in Brackets. Then open the file in your web browser using the Live Preview. Be sure to open up your Browser console as well. You'll see the script currently populates the map with one marker on Lexington, and the popup displays the name of the city.

1. Note that there is already one variable that references Lexington's area (in square miles). You should create a second and third variable to reference the area of a second and third city you'd like to map.

2. Next, you'll notice the script calls a function named `prepareData` and passes the `lexArea` variable as an argument. Modify this statement to pass as arguments all 3 variables referencing the city areas.

3. Complete the `prepareData` function's definition by including all three of the appropriate parameters (i.e., the three variables referencing the cities' areas) within the function's parentheses. 

4. Finish populating the 4 Arrays within the `prepareData` function's body with information from your 2nd and 3rd cities. The final Array, referenced by the `cityAreas` variable, should hold variable names and not hard-coded values like the other Arrays.

5. At the bottom of the `prepareData` function's body, modify the statement calling the function named `mapCities` to pass all four Arrays as arguments.

6. Complete the `mapCities` function to accept the 4 Arrays as parameters. These parameter names should match those used within this function's body.

7. Uncomment and then complete the statement assigning a value to the variable `density`. This statement should call a function named `calcPopDensity` and pass 3 arguments: 1) the city's population, 2) the city's area, and 3) the `units` variable, which has been initially defined as *'miles'*. Note that you'll be continuing to modify the script so this value can be changed to 'km'. 

8. Now write a new function named `calcPopDensity` (outside of the `mapCities` function's body). This function needs to accept 3 values as parameters: a city's population, its area, and the variable `units` designated within the `mapCities` function (i.e., 'miles' or 'units'). Write code within the function's body to first:

    a. determine whether the units are in miles or kilometers and, using conditional logical, then
    
    b. calculate population density using the population and area values before returning the result to the caller (i.e., this value will be assigned to the `density` variable within the `mapCities` function). Your conditional (if/else) statements will need to mathematically convert the miles to kilometers if the value of `units` is changed to be 'km'.
    
9. Finally, uncomment the rest of the popup to now include the calculated value of the population density.

10. Change the `h1` and `h2` tags to update your web document with an appropriate (even fun!) title and subtitle, and edit the text at the bottom of the page (e.g., author and meta information).

11. Sync your final solutions with your remote repository and provide a link within Canvas by the due date: **Thursday, February 5th, 11:00am**.