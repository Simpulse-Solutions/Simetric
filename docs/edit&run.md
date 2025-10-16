## Edit & Run :id=edit&run

In the software Architect, it exist two mode. A Edit Mode for the edition of simulation, to place and modify object. And a Run Mode for simulating in real time the project. You can switch from a mode to the other, by toggling a simple button.

![Middle](Images/Run.png ':size=205') ![Middle](Images/Stop.png ':size=100')

- [Edit mode](#editmode)
- [Run mode](#runmode)
- [Reset](#reset)


## Edit mode :id=editmode
Edit mode

The edit mode is useful to build a 3D scene. You can create and modify an entire 3D environment, with multiple 3D model objects, in order to simulate it. Every object have attibutes and specific I/O, that need to be monitor. You can have more information, in the Inspector, Hierarchy, Library Manager and Material Editor, to fully understand how to use the 3D editor.

In the edit mode, you can also monitor every I/O, to fully simulate your project, thanks to buttons, and communication with PLC. To parameter I/O, Data monitor and Buttons Manager are two tools really useful.

You can parameter your own product too for the simulation, by adding, moving or customize your product. All the product management can be understand, with Vertical Bar, Product Manager and Generators pages.

Eventually, you can implement your own intelligence, with C# code and controller.The controller pages, will explain you all you need to know about it.

## Run mode :id=runmode

>Managing Products

- Manually

To add a product in the 3D viewer, it exists 2 different method :

You can use the 4 tools for run Mode : ADD, REMOVE, PAUSING and MOVE.

<table>
        <tbody><tr>
            <th>Icon</th>
            <th>Description</th>
        </tr>
        <tr>
            <td><img class="image" src="http://10.0.1.47/wp-content/uploads/2023/07/Add.png" alt="Image 3"></td>
            <td>This button will permit you to add a product wherever you want in the simulation. You can see a pre-visualization, when you move your mouse.</td>
        </tr>
        <tr>
            <td><img class="image" src="http://10.0.1.47/wp-content/uploads/2023/07/Remove.png" alt="Image 4"></td>
            <td>This button will remove from the simulation the targeted product.</td>
        </tr>
        <tr>
            <td><img class="image" src="http://10.0.1.47/wp-content/uploads/2023/07/Drag.png" alt="Image 1"></td>
            <td>This button will enable you to drag a product during the simulation.</td>
        </tr>
        <tr>
            <td><img class="image" src="http://10.0.1.47/wp-content/uploads/2023/07/Produce.png" alt="Image 2"></td>
            <td>This button enable you to stop in time an object during the simulation. The product will be fixed and can't move at all.</td>
        </tr>
    </tbody></table>

<video width="800" controls>
  <source src="Medias/Add_Remove.mp4" type="video/mp4">
</video>

At any time in a simulation, you can remove a product by using the "remove product tool" : ![Middle](Images/Remove.png ':size=20') . But you can also move a product at any time, by using the "moving product tool" : . Or by using some keybindings :

<table>
        <tbody><tr>
            <th>Icon</th>
            <th>Description</th>
        </tr>
        <tr>
            <td><img class="image" src="http://10.0.1.47/wp-content/uploads/2023/07/shift-e1689665860414.png" alt="Image 1"></td>
            <td>The product will move vertically.</td>
        </tr>
        <tr>
            <td><img class="image" src="http://10.0.1.47/wp-content/uploads/2023/07/ctrl-e1689665865574.jpg" alt="Image 1"></td>
            <td>This will delete the product from the simulation, but it on per-visualization mode, if he is not on a conveyor. If it was on, it will force the product to be create even if the per-visualization was red.</td>
        </tr>
    </tbody></table>

<video width="800" controls>
  <source src="Medias/GoFckMaiden.mp4" type="video/mp4">
</video>

- Automatically


The second method to add a product in the simulation in the generator of product : ![Middle](Images/Generator.png ':size=20') . you will need to left click on the place where you want your generator, parameter it, to settle how the product will be generated. The way to parameter the generator setting, will be explain here.

Also you can monitor product that will be generated, with the "Spy" ![Middle](Images/Spy.png ':size=20') tools and "follow" tools.

The "Spy" tool, spy on an area and will write in a window every I/O of products, in this zone.

The "Follow" tools, by right clicking on a product, will set and follow the camera on the selected product.

<video width="800" controls>
  <source src="Medias/Generator.mp4" type="video/mp4">
</video>

>Testing objects

In Run mode, you can test every mechanical movement of each object. It is recommended to test everything before connecting your simulation to an automate. Also you have to test if all your cells, conveyor and more are functioning in the right way.

You can test your C# code in the controller, your mechanical groups and other parameter object, your cells and your conveyor.

<video width="800" controls>
  <source src="Medias/Cellmagasin.mp4" type="video/mp4">
</video>

You are able in the Run mode, to test and validate each I/O of your automate, before connecting it. it is useful, to be sure that one of the I/O is not well settle. You can look every I/O that you use, in the Communication window.

>Lauching VR

>Testing with PLC

You can also run your project by using your PLC

## Reset :id=reset

The reset button is really useful, it enable you to reset completely your project after a Run mode.

It resets :

- All mechanical movement from mechanical groups, at send them back to the initialization point.

- All controller.

- All button values at their initial values.

- Specific parameter of some object.

- The execeution of controllers, you can have more information here.

- All the configuration files, you can have more information here.





