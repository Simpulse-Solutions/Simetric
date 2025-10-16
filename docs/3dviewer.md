# 3D Viewer  :id=3dviewer

The 3D viewer is the primary window where you observe your simulation. It is crucial to familiarize yourself with its features and functionality in order to fully comprehend and leverage the software's capabilities.

- [3D viewer](#3dviewer)
	- [Navigation](#navigation)
	- [Control Gizmo](#controlgizmo)
	- [Transformations](#transformations)
	- [Views](#views)
	- [Interaction](#interaction)


## Navigation :id=navigation

To fully utilize the software Architect, we need to first examine the controls for the 3D viewer and other related features.

> Moving

In order to navigate freely in the 3D viewer, you need to move.

You can use the middle click on your mouse or the keybindings "ZQSD".

![Middle](Images/middle.png ':size=200') ![Arrows](Images/Arrows.png ':size=200')

This video show you how to use Button 3 to move your camera in the 3D viewer.

<video width="800" controls>
  <source src="Medias/Button3.mp4" type="video/mp4">
</video>

>Rotate camera

You can also rotate your camera by using the right click on your mouse.

![Middle](Images/right_click.png ':size=200')

This video show you how to use right click to rotate your camera in the 3D viewer.

<video width="800" controls>
  <source src="Medias/ClicDroit.mp4" type="video/mp4">
</video>

>Zoom

Finalmy, you can zoom in and out, by using your mouse wheel on the keybindings "+/-"

![Middle](Images/zoom.png ':size=200') ![Arrows](Images/minus.png ':size=200') ![Arrows](Images/plus.png ':size=200')

This video show you how to use mouse wheel to zoom in and out your camera in the 3D viewer.

<video width="800" controls>
  <source src="Medias/Wheel.mp4" type="video/mp4">
</video>

## Control Gizmo :id=controlgizmo

In the 3D viewer, you have access to four tools located above the 3D view window, enabling you to manipulate your newly added object.

<table>
        <tbody><tr>
            <th>Icon</th>
            <th>Description</th>
        </tr>
        <tr>
            <td><img src="Images/translation.png"></td>
            <td>The translation tool permit you to move along X,Y or Z axis your object.</td>
        </tr>
        <tr>
            <td><img src="Images/Rotation.png"></td>
            <td>The rotation tool permit you to rotate along X,Y or Z axis your object.</td>
        </tr>
        <tr>
            <td><img src="Images/Resized.png"></td>
            <td>The resize tool permit you to up scale, or down scale your object.</td>
        </tr>
        <tr>
            <td><img src="Images/Universal.png"></td>
            <td>The universal tool permit you to move, rotate and resize in one tool an object.</td>
        </tr>
    </tbody></table>
	
	
	
<video width="800" controls>
  <source src="Medias/Move.mp4" type="video/mp4">
</video>

You can not use Gizmo control during run mode, the only two thing that you can, move in run mode, are product with move product tool ![Middle](Images/Move.png ':size=20'), and cell with the moving object tool.

>Local/Global

The Local/Global button enable you to switch the 3D reference, from the scene reference to the object reference.

<video width="800" controls>
  <source src="Medias/Reference.mp4" type="video/mp4">
</video>


## Transformations :id=transformations

>Symetry

![Symetry](Images/Symety.png ':size=75')

This tool enables you to move by symmetry with an axis, a selected object. The video just below, will describe how to use this tool.

<video width="800" controls>
  <source src="Medias/Symmetry.mp4" type="video/mp4">
</video>

>Transform/Rotate

![Symetry](Images/Translate.png ':size=200')

This tool enables you to duplicate, to translate or rotate a selected object. You can choose the number of time, you want to duplicate the object, and how he will be translated or rotated. This tool is more precise than the regular transformation tool in Control Gizmo. The video just below, will describe how to use this tool. 

<video width="800" controls>
  <source src="Medias/Translate.mp4" type="video/mp4">
</video>


## Views :id=views

>Layers

All the setting, just show or unshow elements in the 3D Viewer, they are not deleting from the scene.

![Symetry](Images/Layers.png ':size=125')

<table>
        <tbody><tr>
            <th>Icon</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>Grid</td>
            <td>Show/Unshow the grid in the 3D viewer.</td>
        </tr>
        <tr>
            <td>Controller</td>
            <td>Show/Unshow the controller icon in the 3D viewer.</td>
        </tr>
        <tr>
            <td>Mechanic Blocs</td>
            <td>Show/Unshow the mechanical blocs in the 3D viewer.</td>
        </tr>
        <tr>
            <td>Sky</td>
            <td>Show/Unshow the sky on the 3D viewer. You can choose different types of sky</td>
        </tr>
        <tr>
            <td>Walls</td>
            <td>Show/Unshow walls in the 3D viewer.</td>
        </tr>
        <tr>
            <td>Links</td>
            <td>Show/Unshow the links on conveyor that facilitate positionning in the 3D viewer, thanks to link tools.</td>
        </tr>
        <tr>
            <td>Meca Preview</td>
            <td>Show/Unshow mechanical preview of the mechanical groups in the 3D viewer.</td>
        </tr>
        <tr>
            <td>labels objects</td>
            <td>Show/Unshow the label of an object in the 3D viewer.</td>
        </tr>
    </tbody></table>
	

>Layout

The Layouts is useful to save certain organization of window. For example, the minimal one, minimize all editing window. The User one, is a classic display of all useful window.

>Rendering

The rendering settings; is an option to change the way object are shown. CAO and Wireframe view are present for technical uses.

>Axis Views

The 3D environment contains 3 axis : X,Y and Z. You can adjust your camera, with your mouse with the mouse controls, or by clicking on this icon in the bottom right corner of the 3D viewer.

![Symetry](Images/Perspective.png ':size=50')

It enable you to adjust your camera in function of one specific axis.
It exists two different views, orthographic and perspective view. You can switch between them by clicking on the middle square on the same icon

<video width="800" controls>
  <source src="Medias/Vue.mp4" type="video/mp4">
</video>

>First Person Camera

![Symetry](Images/fps.png ':size=20')
This tool enable you to toggle your view, as a first person view. It is useful to navigate in your simulation, as a real operator. it is also a preview for the VR Simulation.


In FPS mode, you can move the camera by using the arrow keybinding on your keyboard. Press escape, to quit the FPS mode.


<video width="800" controls>
  <source src="Medias/FPS.mp4" type="video/mp4">
</video>

>Camera Preview

![Symetry](Images/Camera.png ':size=20')
This tool enables you to save camera angles, and you can return to this point of view by using this tools. The video just below, will describe how to use this tool.

<video width="800" controls>
  <source src="Medias/Camera Preview.mp4" type="video/mp4">
</video>

>Window Lock

The window lock enables you to lock a certain window, on what is set now. It is really useful to track many data from different object and groups in the data monitor.

![Symetry](Images/Lock.png ':size=150')

## Interaction :id=interaction

In the 3D scene, you can use many different keybindings :

Left click on an object to select it. Then you can have access to the data related to this object, in the Hierarchy, Inspector and Data monitor window.

<table>
        <tbody><tr>
            <th>Action</th>
            <th>Description</th>
        </tr>
        
            <tr><td>Delete</td>
            <td>This will delete the object from your project.</td>
        </tr>
        <tr>
            <td>Duplicate</td>
            <td>This will duplicate your object in the simulation.</td>
        </tr>
        <tr>
            <td>Deactivate</td>
            <td>This will unshow the object from the simulation, and will turn off all his interaction in the simulation.</td>
        </tr>
        <tr>
            <td>Hide</td>
            <td>This will just make invisible the object.</td>
        </tr>
    </tbody></table>


<table>
        <tbody><tr>
            <th>Action</th>
            <th>Description</th>
        </tr>
        
            <tr><td>Create</td>
            <td>Add an object or a group to the simulation.</td>
        </tr>
        <tr>
            <td>Convert to</td>
            <td>Convert the last object added to a desired object or groups.</td>
        </tr>
        <tr>
            <td>Delete All products</td>
            <td>Delete all products in the simulation.</td>
        </tr>
    </tbody></table>

All thoses interactions can be done in the hierarchy as well.
