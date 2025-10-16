# Groups :id=groups



Such as a section, you can drag other object and groups, in a group. You can create a group from the 3D viewer, or by the Hierarchy, with a right click.

It exists two types of groups : standard and mechanical. Even if they are different, both of them has some common attributes.

<table>
    <tbody><tr>
        <th>Name</th>
        <th>Icon</th>
        <th>Description</th>
    </tr>
    <tr>
        <td><a href="/#/groups.md?id=section">Section</a></td>
        <td><img src="Images/0121.png"></td>
        <td>Group in charge of all simulation groups</td>
    </tr>
    <tr>
        <td><a href="/#/groups.md?id=standard">Standard</a></td>
        <td><img src="Images/0141.png"></td>
        <td>Classic groups with no exclusive features.</td>
    </tr>
    <tr>
        <td><a href="/#/groups.md?id=simple">Simple</a></td>
        <td><img src="Images/0142.png"></td>
        <td>Mechanical groups that can rotate and translate with a given speed.</td>
    </tr>
    <tr>
        <td><a href="/#/groups.md?id=drive">Drive</a></td>
        <td><img src="Images/0142.png"></td>
        <td>Mechanical groups that can translate with a given acceleration.</td>
    </tr>
    <tr>
        <td><a href="/#/groups.md?id=hydraulic">Hydraulic</a></td>
        <td><img src="Images/0142.png"></td>
        <td>Mechanical groups that can translate with a given pressure by a hydraulic pump.</td>
    </tr>
    <tr>
        <td><a href="/#/groups.md?id=trajectory">Trajectory</a></td>
        <td><img src="Images/0142.png"></td>
        <td>Mechanical groups that can translate by following a point path.</td>
    </tr>
    <tr>
        <td><a href="/#/groups.md?id=scaler">Scaler</a></td>
        <td><img src="Images/0142.png"></td>
        <td>Mechanical groups that can scale up or down.</td>
    </tr>
    
</tbody></table>

>Mechanical groups

![Middle](Images/mechanical.png ':size=80')

Mechanical groups are specific groups, which can move object, within the groups, in 3D space. They are useful to reproduce physics movement in an industrial simulation, or just to move object in the simulation., such as translation, a rotation, or the movement of a industrial robot. 

Each mechanical groups appears in the 3D viewer, as a cube with a motor in it. This cube can be un-show, by un-validate the square in the horizontal bar, Bar> Layers>Show Mechanical Bloc. As a standard group, you can move everything at the same time, by using the control gizmo.

![Middle](Images/CompanionCube.png ':size=200')

You can a preview of the mechanical groups, by validate the square in the horizontal bar, Bar> Layers>Show Meca Preview.

![Middle](Images/Preview.png ':size=200')

<table>
        <tbody><tr>
            <th>Attributes</th>
            <th>Description</th>
        </tr>
        
            <tr><td>Init Position</td>
            <td>3D coordinate of the initial position of the group. When you reset the environment, the groups will be reset at this position..</td>
        </tr>
        <tr>
            <td>Max_Value</td>
            <td>The maximum value in millimeter or radians possible for the group.</td>
        </tr>
            <tr><td>Min_Value</td>
            <td>The minimum value in millimeter or radians possible for the group.</td>
        </tr>
            <tr><td>Direction</td>
            <td>If this value is negative, the groups will move backward. If the value is different from 1, maximum and minimum value will be multiplied together.</td>
        </tr>
            <tr><td>Scaling</td>
            <td>Factor that converte in adequation the maximum and minium values.</td>
    </tr></tbody></table>

![Middle](Images/init.png ':size=500')

Additionally, you have the flexibility to change the initial position and scale of the objects within the group.

![Middle](Images/datas.png ':size=500')

In the data monitor window, you can observe and analyze I/O about the mechanical groups, including their position encoder, speed, and more. Each mechanical groups have specific I/O. Even They all have a common DI : "DI_Encoder", it is an encoder, in millimeter for a translation, in radians for a rotation. It can be incremented or decremented, in function of the way.


# Section :id=section

>What is it ?

The section are just visual separator in the hierarchy, this is useful to make distinct two groups distinct in a project. You can drag the object and groups that you want to sort in the section you want. A section do not interfere with the simulation.

>Inspector

<table>
        <tbody><tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>Name</td>
            <td>Name of the current section.</td>
        </tr>
    </tbody></table>

>Data Monitor

No attributes for a section.

>Specifies

When you are loading your project, you can decide, which section will be loaded. You can unloaded one or more section, in order to minimize the use of data.

>Example



# Standard :id=standard

>What is it ?

Standard groups is similar to a section. They do not appear in the 3D Viewer. They are here to gather object together. You can move a entire groups, at the same time, when you select the group.

>Inspector

<table>
        <tbody><tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>Name</td>
            <td>Name of the current section.</td>
        </tr>
    </tbody></table>

>Data Monitor

No attributes for a section.

>Specifies

When you are loading your project, you can decide, which section will be loaded. You can unloaded one or more section, in order to minimize the use of data.

>Example

<video width="800" controls>
  <source src="Medias/Together.mp4" type="video/mp4">
</video>



# Mechanical Simple :id=simple

The bascule mechanical group is used to rotate every object linked to it in a specific direction. All the parameters, such as speed, direction, and maximum rotation value, can be configured using the inspector window.

>What is it ?

The Mechanical Simple groups is used to rotate and translate every object linked to it in a specific direction.

>Inspector

<table>
        <tbody><tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>Name</td>
            <td>Name of the current section.</td>
        </tr>
        <tr>
            <td>Position</td>
            <td>Position in the 3D environment.</td>
        </tr>
        <tr>
            <td>Connection Id</td>
            <td>Connection to an automate</td>
        </tr>
        <tr>
            <td>Alias Element</td>
            <td>Prefixe given to all groups attributes in order to identify them easily.</td>
        </tr>
        <tr>
            <td>Is_Node</td>
            <td>Show all attributes from the groups in the data monitor.</td>
        </tr>
        <tr>
            <td>Initial Position</td>
            <td>Initial position of the group.</td>
        </tr>
        <tr>
            <td>Physicalize</td>
            <td>Will not pass through object that physicalize too.</td>
        </tr>
        <tr>
            <td>Scaling</td>
            <td>Scale by the value all element in the group</td>
        </tr>
        <tr>
            <td>Description</td>
            <td>Description given to the group.</td>
        </tr>
        <tr>
            <td>Value Max</td>
            <td>Maximum value that the mechanical group can reach.</td>
        </tr>
        <tr>
            <td>Value Min</td>
            <td>Minimum value that the mechanical group can reach.</td>
        </tr>
           
            <tr><td>Speed</td>
            <td>High speed in m/s.</td>
        </tr>
        <tr>
            <td>Speed_2</td>
            <td>low speed in m/s.</td>
        </tr>
        <tr>
            <td>Direction</td>
            <td>Direction where the group will move.</td>
        </tr>
        <tr>
            <td>Bistable</td>
            <td>Got many different stable points.</td>
        </tr>
        <tr>
            <td>Rotation Mode</td>
            <td>Switch between translation and rotation.</td>
        </tr>
    </tbody></table>

>Data Monitor

<table>
        <tbody><tr>
            <th>I/O</th>
            <th>Description</th>
        </tr>
        
            <tr><td>DI_Encoder</td>
            <td>Position in mm or mrad.</td>
        </tr>
        
            <tr><td>DO_Reset</td>
            <td>Reset DI_encoder to 0.</td>
        </tr>
        
            <tr><td>DO_Reset_Value</td>
            <td>Reset DI_encoder to the value.</td>
        </tr>
        
            <tr><td>Do_FreeWheel</td>
            <td>Switch the group as a free wheel.</td>
        </tr>
        
            <tr><td>DO_Lower_HS</td>
            <td>Go to the min value at high speed.</td>
        </tr>
        
            <tr><td>DO_Lower_LS</td>
            <td>Go to the min value at low speed.</td>
        </tr>
		
            <tr><td>DO_Raise_HS</td>
            <td>Go to the max value at high speed.</td>
        </tr>
		
            <tr><td>DO_Raise_LS</td>
            <td>Go to the max value at low speed.</td>
        </tr>
		
            <tr><td>DI_High</td>
            <td>Return of the max value.</td>
        </tr>
		
            <tr><td>DI_Low</td>
            <td>Return of the min value.</td>
		</tr>
    </tbody></table>

>Specifies



>Example


# Mechanical Drive :id=drive

>What is it ?

The drive mechanical group is used to move or rotate objects in a specific direction, with an acceleration. You can configure various parameters such as speed, direction, and more using the inspector window.

>Inspector

<table>
        <tbody><tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>Name</td>
            <td>Name of the current section.</td>
        </tr>
        <tr>
            <td>Position</td>
            <td>Position in the 3D environment.</td>
        </tr>
        <tr>
            <td>Connection Id</td>
            <td>Connection to an automate</td>
        </tr>
        <tr>
            <td>Alias Element</td>
            <td>Prefixe given to all groups attributes in order to identify them easily.</td>
        </tr>
        <tr>
            <td>Is_Node</td>
            <td>Show all attributes from the groups in the data monitor.</td>
        </tr>
        <tr>
            <td>Initial Position</td>
            <td>Initial position of the group.</td>
        </tr>
        <tr>
            <td>Physicalize</td>
            <td>Will not pass through object that physicalize too.</td>
        </tr>
        <tr>
            <td>Scaling</td>
            <td>Scale by the value all element in the group</td>
        </tr>
        <tr>
            <td>Description</td>
            <td>Description given to the group.</td>
        </tr>
        <tr>
            <td>Value Max</td>
            <td>Maximum value that the mechanical group can reach.</td>
        </tr>
        <tr>
            <td>Value Min</td>
            <td>Minimum value that the mechanical group can reach.</td>
        </tr>
           
            <tr><td>Speed</td>
            <td>High speed in m/s.</td>
        </tr>
        <tr>
            <td>Acceleration</td>
            <td>Acceleration in m²/s.</td>
        </tr>
        <tr>
            <td>Direction</td>
            <td>Direction where the group will move.</td>
        </tr>
        <tr>
            <td>Rotation Mode</td>
            <td>Switch between translation and rotation.</td>
        </tr>
    </tbody></table>

>Data Monitor

<table>
        <tbody><tr>
            <th>I/O</th>
            <th>Description</th>
        </tr>
            <tr><td>DI_Encoder</td>
            <td>Position in mm or mrad.</td>
        </tr>
            <tr><td>DO_Reset</td>
            <td>Reset DI_encoder to 0.</td>
        </tr>
            <tr><td>DO_Reset_Value</td>
            <td>Reset DI_encoder to the value.</td>
        </tr>
            <tr><td>Do_FreeWheel</td>
            <td>Switch the group as a free wheel.</td>
        </tr>
            <tr><td>DO_Jog_Forward</td>
            <td>Go to the maximum value.</td>
        </tr>
            <tr><td>DO_Jog_backward</td>
            <td>Go to the minimum value.</td>
        </tr>
            <tr><td>DO_Jog_Enable</td>
            <td>Go to the max value.</td>
        </tr>
            <tr><td>DO_MoveTo</td>
            <td>Move the value in mm.</td>
        </tr>
            <tr><td>DO_Start</td>
            <td>Start the mechanical group.</td>
        </tr>
            <tr><td>DI_Moving</td>
            <td>Read if the group is moving forward.</td>
        </tr>
            <tr><td>DI_Reverse</td>
            <td>Read if the group is moving backward.</td>
		</tr>
            <tr><td>Do_Speed_0_1000</td>
            <td>Fix a speed </td>
        </tr>
            <tr><td>DI_Speed_0_1000</td>
            <td>Read the group speed.</td>
        </tr>
            <tr><td>DI_RealSpeed</td>
            <td>Read the real speed in m/s</td>
        </tr>
            <tr><td>DI_Position_OK</td>
            <td>Read if the position of the group match the end position</td>
        </tr>
            <tr><td>DI_High</td>
            <td>Return of the max value.</td>
        </tr>
            <tr><td>DI_Low</td>
            <td>Return of the min value.</td>
		</tr>
            <tr><td>DO_Acceleration</td>
            <td>Set the Accelearion to this value.</td>
        </tr>
            <tr><td>DI_Up_Mvt1</td>
            <td>Read the movement 1.</td>
        </tr>
            <tr><td>DI_Down_Mvt1</td>
            <td>Read the movement 1.</td>
		</tr>
    </tbody></table>

>Specifies



>Example




# Mechanical Hydraulic :id=hydraulic

>What is it ?

The hydraulic mechanical group is used to rotate and translate every object linked to it. The groups depends on a hydraulic pumps, with pressure and debit. All the parameters, such as speed, direction, and more, can be configured using the inspector window.

>Inspector

<table>
        <tbody><tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>Name</td>
            <td>Name of the current section.</td>
        </tr>
        <tr>
            <td>Position</td>
            <td>Position in the 3D environment.</td>
        </tr>
        <tr>
            <td>Connection Id</td>
            <td>Connection to an automate</td>
        </tr>
        <tr>
            <td>Alias Element</td>
            <td>Prefixe given to all groups attributes in order to identify them easily.</td>
        </tr>
        <tr>
            <td>Is_Node</td>
            <td>Show all attributes from the groups in the data monitor.</td>
        </tr>
        <tr>
            <td>Initial Position</td>
            <td>Initial position of the group.</td>
        </tr>
        <tr>
            <td>Physicalize</td>
            <td>Will not pass through object that physicalize too.</td>
        </tr>
        <tr>
            <td>Scaling</td>
            <td>Scale by the value all element in the group</td>
        </tr>
        <tr>
            <td>Description</td>
            <td>Description given to the group.</td>
        </tr>
        <tr>
            <td>Value Max</td>
            <td>Maximum value that the mechanical group can reach.</td>
        </tr>
        <tr>
            <td>Value Min</td>
            <td>Minimum value that the mechanical group can reach.</td>
        </tr>
           
            <tr><td>Speed</td>
            <td>High speed in m/s.</td>
        </tr>
        <tr>
            <td>Speed_2</td>
            <td>Low speed in m/s.</td>
        </tr>
        <tr>
            <td>Direction</td>
            <td>Direction where the group will move.</td>
        </tr>
        <tr>
            <td>Bistable</td>
            <td>Got many different stable points.</td>
        </tr>
        <tr>
            <td>Rotation Mode</td>
            <td>Switch between translation and rotation.</td>
        </tr>
        <tr>
            <td>Pressure Min</td>
            <td>Minimum pressure needed to start the mechanical group.</td>
        </tr>
        <tr>
            <td>Target</td>
            <td>target the hydraulic pump.</td>
        </tr>
    </tbody></table>

>Data Monitor

<table>
        <tbody><tr>
            <th>I/O</th>
            <th>Description</th>
        </tr>
            <tr><td>DI_Encoder</td>
            <td>Position in mm or mrad.</td>
        </tr>
            <tr><td>DO_Reset</td>
            <td>Reset DI_encoder to 0.</td>
        </tr>
            <tr><td>DO_Reset_Value</td>
            <td>Reset DI_encoder to the value.</td>
        </tr>
            <tr><td>Do_FreeWheel</td>
            <td>Switch the group as a free wheel.</td>
        </tr>
            <tr><td>DO_Lower_HS</td>
            <td>Go to the min value at high speed.</td>
        </tr>
            <tr><td>DO_Lower_LS</td>
            <td>Go to the min value at low speed.</td>
        </tr>
            <tr><td>DO_Raise_HS</td>
            <td>Go to the max value at high speed.</td>
        </tr>
            <tr><td>DO_Raise_LS</td>
            <td>Go to the max value at low speed.</td>
        </tr>
            <tr><td>Do_Speed_0_1000</td>
            <td>Fix a speed </td>
        </tr>
            <tr><td>DI_Speed_0_1000</td>
            <td>Read the group speed.</td>
        </tr>
            <tr><td>DI_RealSpeed</td>
            <td>Read the real speed in m/s</td>
        </tr>
            <tr><td>DI_High</td>
            <td>Return of the max value.</td>
        </tr>
            <tr><td>DI_Low</td>
            <td>Return of the min value.</td>
		</tr>
            <tr><td>DI_Pressure_0_1000</td>
            <td>Read the main pressure</td>
		</tr>
            <tr><td>DI_Pressure2_0_1000</td>
            <td>Read the second pressure.</td>
		</tr>
    </tbody></table>

>Specifies



>Example





# Mechanical Trajectory :id=trajectory

>What is it ?

The trajectory mechanical group is used to move objects linked to it by following a predefined list of points. All the parameters, including speed, direction, and the list of checkpoints, can be configured using the inspector window.

>Inspector

<table>
        <tbody><tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>Name</td>
            <td>Name of the current section.</td>
        </tr>
        <tr>
            <td>Position</td>
            <td>Position in the 3D environment.</td>
        </tr>
        <tr>
            <td>Connection Id</td>
            <td>Connection to an automate</td>
        </tr>
        <tr>
            <td>Alias Element</td>
            <td>Prefixe given to all groups attributes in order to identify them easily.</td>
        </tr>
        <tr>
            <td>Is_Node</td>
            <td>Show all attributes from the groups in the data monitor.</td>
        </tr>
        <tr>
            <td>Initial Position</td>
            <td>Initial position of the group.</td>
        </tr>
        <tr>
            <td>Physicalize</td>
            <td>Will not pass through object that physicalize too.</td>
        </tr>
        <tr>
            <td>Scaling</td>
            <td>Scale by the value all element in the group</td>
        </tr>
        <tr>
            <td>Description</td>
            <td>Description given to the group.</td>
        </tr>
        <tr>
            <td>Value Max</td>
            <td>Maximum value that the mechanical group can reach.</td>
        </tr>
        <tr>
            <td>Value Min</td>
            <td>Minimum value that the mechanical group can reach.</td>
        </tr>
           
            <tr><td>Speed</td>
            <td>High speed in m/s.</td>
        </tr>
        <tr>
            <td>Acceleration</td>
            <td>Acceleration in m²/s.</td>
        </tr>
        <tr>
            <td>List Points</td>
            <td>List of checkpoint.</td>
        </tr>
        <tr>
            <td>List Orientations</td>
            <td>List of checkpoint angles.</td>
        </tr>
        <tr>
            <td>Is loop</td>
            <td>Make a loop.</td>
        </tr>
    </tbody></table>


>Data Monitor
<table>
        <tbody><tr>
            <th>I/O</th>
            <th>Description</th>
        </tr>
            <tr><td>DI_Encoder</td>
            <td>Position in mm or mrad.</td>
        </tr>
            <tr><td>DO_Jog_Forward</td>
            <td>Go to the maximum value.</td>
        </tr>
            <tr><td>DO_Jog_backward</td>
            <td>Go to the minimum value.</td>
        </tr>
            <tr><td>DO_Jog_Enable</td>
            <td>Go to the max value.</td>
        </tr>
            <tr><td>DO_MoveTo</td>
            <td>Move the value in mm.</td>
        </tr>
            <tr><td>DO_Start</td>
            <td>Start the mechanical group.</td>
        </tr>
            <tr><td>DI_Moving</td>
            <td>Read if the group is moving forward.</td>
        </tr>
            <tr><td>DI_Reverse</td>
            <td>Read if the group is moving backward.</td>
		</tr>
            <tr><td>Do_Speed_0_1000</td>
            <td>Fix a speed </td>
        </tr>
            <tr><td>DI_Speed_0_1000</td>
            <td>Read the group speed.</td>
        </tr>
            <tr><td>DI_RealSpeed</td>
            <td>Read the real speed in m/s</td>
        </tr>
    </tbody></table>

>Specifies



>Example


# Mechanical Scaler :id=scaler

>What is it ?

The scaler mechanical group is used to scale up or down every object linked to it in a specific direction.  All the parameters can be configured using the inspector window.

>Inspector

<table>
        <tbody><tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>Name</td>
            <td>Name of the current section.</td>
        </tr>
        <tr>
            <td>Position</td>
            <td>Position in the 3D environment.</td>
        </tr>
        <tr>
            <td>Connection Id</td>
            <td>Connection to an automate</td>
        </tr>
        <tr>
            <td>Alias Element</td>
            <td>Prefixe given to all groups attributes in order to identify them easily.</td>
        </tr>
        <tr>
            <td>Is_Node</td>
            <td>Show all attributes from the groups in the data monitor.</td>
        </tr>
        <tr>
            <td>Initial Position</td>
            <td>Initial position of the group.</td>
        </tr>
        <tr>
            <td>Physicalize</td>
            <td>Will not pass through object that physicalize too.</td>
        </tr>
        <tr>
            <td>Scaling</td>
            <td>Scale by the value all element in the group</td>
        </tr>
        <tr>
            <td>Description</td>
            <td>Description given to the group.</td>
        </tr>
        <tr>
            <td>Value Max</td>
            <td>Maximum value that the mechanical group can reach.</td>
        </tr>
        <tr>
            <td>Value Min</td>
            <td>Minimum value that the mechanical group can reach.</td>
        </tr>
        <tr>
            <td>Direction</td>
            <td>Direction where the group will move.</td>
        </tr>
    </tbody></table>

>Data Monitor

<table>
        <tbody><tr>
            <th>I/O</th>
            <th>Description</th>
        </tr>
            <tr><td>DO_MoveTo</td>
            <td>Scale the group by the value.</td>
        </tr>
    </tbody></table>

>Specifies



>Example

<video width="800" controls>
  <source src="Medias/scale.mp4" type="video/mp4">
</video>