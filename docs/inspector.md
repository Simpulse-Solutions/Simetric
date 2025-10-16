# Inspector :id=inspector

The inspector window show you the useful 3D information about an object of the hierarchy. the information show change in function of what object you selected. it exist many different types of objects : groups, mechanical groups, transitive, sensors, controllers and others.

>Object Inspector

For example, if you select a button box, we will be able to see this :

![Middle](Images/InspectorButtonBox.png ':size=400')

You can see, the position and the orientation in the 3D environment of the controller, the number of the controller and it s name.

All the types of object will always have those data in the inspector window :

<table>
        <tbody><tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>Position </td>
            <td>This is the coordinate of your object in the space of the 3D viewer, you can translate as with the translation tool, our object.</td>
        </tr>
        
            <tr><td>Orientation </td>
            <td>This is the rotate coordinate of your object in the space of the 3D viewer, you can rotate as with the rotation tool, our object.</td>
        </tr>
        
            <tr><td>Dimension </td>
            <td>This is the dimension of your object in the space of the 3D viewer, you can scale up or down as with the resize tool, our object.</td>
        </tr>
            <tr><td>Description </td>
            <td> This enables you to write a quick presentation of your object, that will appear on the Data monitor window.</td>
        </tr>
            <tr><td>Label </td>
            <td> This enables you to write a little tag, that will appears on top of the object on the scene.</td>
        </tr>
            <tr><td>UseEulerOrientation</td>
            <td>Should be always on. Set the rotation and translation measures as meter and degrees.</td>
        </tr>
    </tbody></table>

>Groups information

One of the most important feature of the inspector window, is that permit you to link a group of the hierarchy to an automate. In order to permit to the automate, to have access to all the variable in the group.

<table>
        <tbody><tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>Automate Number</td>
            <td>Link your object to an automate.</td>
        </tr>
        
            <tr><td>Alias_Element</td>
            <td>Give a name to all objects parameter in order to monitor easily those parameters. For example, "conveyor_one", as alias_element, will give to all "conveyor_one." at the beginning of all parameters.</td>
        </tr>
</tbody></table>

All groups have in common also the Alias_element and IsNode attributes.

If they are a specific attributes for an object, it will be explain in the groups & object section.

>Example

<video width="800" controls>
  <source src="Medias/Model.mp4" type="video/mp4">
</video>


Here is an example of a specific attributes with a button box, the "model" attributes. It enables you to change the appearances of your button box. 
