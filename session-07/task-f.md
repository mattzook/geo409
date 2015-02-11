#Task F: JavaScript Objects

**Instructions:** First, copy over the directory [https://github.com/newmapsplus/geo409/session-07/task/](https://github.com/newmapsplus/geo409/session-07/task/) into the root directory of your personal *geo409* Git repository and rename it to *task-f/* -- just like you previously did with tasks a to e. Modify the *index.html* within this directory to fulfill the requirements listed below. 

The goal of this task is to build a map with markers on three cities within three different US states. The popup of each marker will display the text in a unique color dependent upon the state in which the city marker is located.

Save your changes to your *index.html* file and **commit changes to your local GitHub repository** as you work. Begin your coding beneath line 93 containing the comment `begin writing/editing Task F code here`. 

So far in Geo409, the modules have used the Array data type to structure and store information about various cities for web mapping using a Leaflet map. This lab will make use of JavaScript objects to achieve this, as well as to bring together the looping and conditional logic practiced within earlier modules.

**Assemble the data structures**

1. First declare a variable named `cities` and assign an Array to this variable. The `cities` Array will contain three JavaScript objects, each of which will represent a different city.

2. Each city object will be made of two properties. The the name of the first property will be `name`, and its associated value will be a String value of the name of the city (e.g., `name: "Louisville"`). The name of the second property within each city object will `properties`, and its value will be another object (e.g., `properties: { /* object properties go here }`). The `properties` object will itself hold three additional properties: `coordinates`, `population`, and `state`, which are respectively associated with an Array value, a Numeric value, and a String value. For example, an object representing the city of Louisville will look like this:
```javascript
    {
        name: "Louisville",
        properties: {
            coordinates: [38.25, -85.7667],
            population: 756832,
            state: "KY"
        }
    }
```
Finish building your cities Array to contain three such city objects.

3. Next, construct a *for* loop that will loop through the three elements (in this case JavaScript objects) contained within the `cities` Array.

4. Within the loop, try writing a couple *console.log()* statements, saving your file and testing the result by refreshing your browser with the JavaScript Console open as you do.  First, try logging to the console each element within the `cities` Array:

    ```javascript
        console.log(cities[i]);
    ```

    After refreshing your browser's web page, within the JavaScript Console you should see three lines of output that look something like `Object {name: "Louisville", properties: Object}`. You've essentially logged the contents of each of your `cities` Array objects to the console. By clicking on the grey arrows to the left you can drill down into the nested structure of these objects:

    ![Nested structure of the cities objects logged to the Console](assets/console-log-cities.png)

    Second, see if you can access just the `properties` of each city object with a *console.log()* statement using either bracket or dot notation, (i.e., `console.log(cities[i].properties);`). Note that you may wish to comment out or delete the previous *console.log()* statement so the output doesn't get cluttered and confusing. Examine the output of this second *console.log* statement (you should recognize the properties you encoded within your `cities` Array's objects).

    Okay, now that you can access these properties, assign them to a new variable named `props`. This will act as a shorthand for accessing these properties further on in the script, so you don't need to write `cities[i].properties` each time but can simply write `props`. You can verify that this statement has assigned the each city's `properties`'s properties to the variable by writing yet another *console.log* statement (i.e., `console.log(props)`). Hint: if you haven't already, get in the habit of writing lots of these *console.log* statements, saving your file, and examining the output in the web browser.

    After creating the `props` variable within the, create a variable for the content of our map marker popups, and assign a simple String for now. Then write the mysterious `L.marker( ...` code we've been using so far within the Tasks. After reading Module 7, you may now recognize the `.marker()` as a method! We're going to pass one argument with this method call: the value of the `coordinates` property currently held within our `props` variable. Your *for* loop should now contain the following code:

    ```javascript
        var props = cities[i].properties;

        var popup = "I am a temporary String value";

        L.marker(props.coordinates).addTo(map)
                .bindPopup(popup);   
    ```
    Save your document and test the map in the browser. Your map should now contain the three markers, each with a popup that says something useless like "I am a temporary String value." Verify that there are no errors in the Console. Also note that you may need to adjust the values for the map's center coordinates and zoom level, found on lines 80 and 81 of the Task F *index.html* file. The zoom level is an integer between 4 and 12 that indicates how far zoomed-in the map will be -- 4 being global scale and 12 the scale of an urban neighborhood.

5. Instead of assigning a string to the `popup` variable, we want to instead construct the popup dynamically using a function. Declare the *buildPopup* function (outside of the *for* loop). It will need to achieve the following: a) accept the three arguments, b) use conditional if/else statements to determine which state a particular city is found it, c) create and assign a unique String value to a variable named `colorClass`. You'll want a different unique String value for each of the potential cities. 

    Furthermore, these values need to correspond with CSS class definitions contained in the CSS style rules at the top of the document. You'll notice that three have been provided as examples:

    ```css
        .blue {
            color: #165bb6;
        }
        .red {
            color: #cc0000;
        }
        .purple {
            color: #b6165b; 
        }
    ```
    You may wish to create new CSS style rules and use different colors for your map (you can determine the hexidecimal values for various colors from such a website as [http://www.color-hex.com/](http://www.color-hex.com/)).          

    After the conditional statements are done executing, the *buildPopup* function should return the following string (you should copy this code exactly):

    ```javascript
        "<div class='"+colorClass+"'><b>"+name+"</b><br>"+
        "<b>Population</b>: "+pop.toLocaleString()+"<div>";
    ```
    
6. Once your `buildPoup` function is declared, the code within it will not run unless we *call* the function from somewhere. In this case,  use it to assign a value to the `popup` variable within the `for` loop. You can pass the neccesary argument using the `props` variable. Once you call the function, if the popups don't render properly or you find error messages in the Console, there likely is an error within your function's body. Use `console.log` and the error messages in the Console to debug the function step-by-step.

7. Once you have the map working (each popup should be uniquely colored based upon the value contained with the `state` property of each city), change the `h1` and `h2` tags to update your web document with an appropriate (even fun!) title and subtitle, and edit the text at the bottom of the page (e.g., author and meta information).

11. Sync your final solutions with your remote repository and provide a link within Canvas by the due date: **Tuesday, February 10th, 11:00am**.


