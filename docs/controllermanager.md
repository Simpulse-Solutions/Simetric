## Controller  Manager :id=controllermanager

- [Controller Manager](#controllermanager)
	- [Coding](#coding)
	- [Compiling](#compiling)
	- [Controller](#controller)
	- [Function](#function)
	- [Content Manager](#contentmanager)
	- [CO_Object](#co_object)
	- [Code Example](#codeexample)

## Coding :id=coding

It is possible to code in Architect, with controller. When you open a controller, by right clicking and choosing "code". You will have access to the code environment in C#. You need to know the basic of C# in order to code in Architect.

![Middle](Images/Controller.jpg ':size=500')

In this section, you will learn useful function, and specific code in Architect, not the C# basic.

## Compiling :id=compiling

You must often compile your C# code, to make sure they're is no native error in your code. Such as non defined variable, or more.

## Controller :id=controller

Controllers are the servos responsible for controlling specific aspects of the simulation. They serve as the central component for monitoring and managing the simulation. To ensure a seamless simulation experience, controllers must be programmed using C# and specialized tools.

>How to access ?

To access this window, right-click on the controller in the hierarchy and select "Information" from the context menu. This will open the window where you can view and manage the details and settings related to the controller.

This window consists of four main parts: the top toolbar, the coding environment, the parameter controller, and the local variables section. Each of these components serves a distinct purpose in managing and customizing the controller's behavior and functionality.

![Middle](Images/Controller.jpg ':size=500')

>Top Bar

The Top bar is separated in two section : one is composed of the name of the current selected controller, a scrolling menu to switch between all controller and a target buttons to see in the 3D environment where is the controller. 

The second part, composed of the "Compile" button, which compile your code in the console, and the "Replace", which replace in the 3D environment the controller's code.

>Global Variables

The parameter controller window displays all the variables associated with objects present in the simulation. For each controller, you need to define the variables it will use from the objects in the simulation. For instance, if you have a conveyor, you can add variables to the parameter controller window that control the conveyor's speed or direction (forward or backward). This allows you to effectively manage and control the behavior of objects in the simulation by defining the necessary variables in the parameter controller.

![Middle](Images/ParameterController.png ':size=500')

<table>
    <tbody><tr>
        <th>Name</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>Variable</td>
        <td>Name of the variable.</td>
    </tr>
    <tr>
        <td>Object</td>
        <td>Associated object of the variable.</td>
    </tr>
    <tr>
        <td>Attribut</td>
        <td>Attribut of the variable.</td>
    </tr>
    <tr>
        <td>Parameter</td>
        <td>Show the associated parameter of the variable</td>
    </tr>
    <tr>
        <td>Value</td>
        <td>Show the value.</td>
    </tr>
</tbody></table>

This window allows you to establish a connection between the simulation environment and your code. You can access objects such as cells or conveyors and choose to monitor or observe specific variables associated with those objects.

![Middle](Images/parameter_use.png ':size=500')

To use these variables, you need to add a new variable by clicking on the "add" button. Then, you can select the object and choose which variable you want to add from that object.

<video width="800" controls>
  <source src="Medias/ParameterController.mp4" type="video/mp4">
</video>

by using the content manager method.

>Local Variables

This window allows you to view the current state of each local variable present in your code. It provides you with a comprehensive overview of the values and status of the local variables, enabling you to monitor and track their state during the execution of your code.

![Middle](Images/LocalVariable.png ':size=500')

>Coding environment

The coding environment is where you write your code using the C# programming language. You can declare variables in the parameter controller or within your code. After writing your code, you need to compile it in order to upload it to the simulation and make it functional.

![Middle](Images/codingEnvironment.png ':size=500')

## Function :id=function


>Looping

Thoses functions are mandatory in your code, otherwise, il will never run.

- void _Init()

This method is the initialization of the controller, where you can set the initial state of each variable at the beginning of the simulation. It is optional to leave the Init() function empty if desired.

public void _Init()

   {

 }

- void _Loop()

This method is called repeatedly, allowing the program to continuously execute a set of instructions. Typically, within this method, you will utilize the "switch"/"case" functions, which enable you to execute specific code based on the current state of the simulation. This is achieved by using a variable that changes according to different stages or events occurring within the simulation.

public void _Loop()

{

    //   Log(g7Step);
    Btn_Step = (short)g7Step;
    TOK_Aval1 = Btn_Ok;
    TOK_Aval2 = Btn_Ok;
    Speed = 1000;
    if(Btn_Reset)

    {
        Avance = false;
        g7Step = 0;
    }


    switch(g7Step)
    {
        case 0:
        {
            //commandes
            Avance = false;
            //conditions
            if(DTR_Amont) {g7Step = 1; break;}
            break;
        }
        case 1:
        {
            //commandes
            Avance = Btn_Ok && DTR_Amont && AU_OK;
            ATR_Amont = true;
            Direction = Direction_Amont;
            //conditions
            if(Cell_In) {g7Step = 2; break;}
            break;
        }
        case 2:
        {
            //commandes
            Avance = Btn_Ok && DTR_Amont && AU_OK;
            ATR_Amont = true;
            //conditions
            if(!Cell_In) {g7Step = 3; break;}
            break;
        }
      case 3:
        {
            //commandes
            Avance = false;
            ATR_Amont = false;
            FTR_Amont = true;
            //conditions
            if(Evac) {g7Step = 11; break;}
            if(Sortie2 || Direction == 2) {g7Step = 21; break;}
            if(!Sortie2) {g7Step = 11; break;}
            break;
        }
      case 11:
       {
           Descente = !Cell_Bas && AU_OK;
           if(Cell_Bas) {g7Step = 12; break;}
            break;
       }
      case 12:
        {
            //commandes
            Avance = false;
            DTR_Aval1 = true;
            //conditions
            if(ATR_Aval1) {g7Step = 13; break;}
            break;
        }
      case 13:
        {
            //commandes
            FTR_Amont = false;
            Avance = ATR_Aval1 && AU_OK;
            //conditions
            if(FTR_Aval1) {g7Step = 14; break;}
            break;
        }
      case 14:
        {
            //commandes
            Avance = false;
            DTR_Aval1 = false;
            //conditions
            if(true) {g7Step = 0; break;}
            break;
        }
      case 21:
       {
            Montee = !Cell_Haut && AU_OK;
            if(Cell_Haut) {g7Step = 22; break;}
            break;
       }
      case 22:
        {
            //commandes
            Avance = false;
            DTR_Aval2 = true;
            //conditions
            if(ATR_Aval2) {g7Step = 23; break;}
            break;
        }
      case 23:
        {
            //commandes
            FTR_Amont = false;
            Avance = ATR_Aval2 && AU_OK;
            //conditions
            if(FTR_Aval2) {g7Step = 24; break;}
            break;
        }
      case 24:
        {
            //commandes
            Avance = false;
            DTR_Aval2 = false;
            //conditions
            if(true) {g7Step = 25; break;}
            break;
        }
      case 25:
        {
            //commandes
            Avance = false;
            DTR_Aval2 = false;
            Descente = !Cell_Bas && AU_OK;
            //conditions
            if(Cell_Bas) {g7Step = 0; break;}
            break;
        }
    }
}

>Standard

They are the standard functions already created and tested in other simulation

void Log()

This method writes a log entry indicating that the controller is currently active. You can customize the content of the log entry to include information such as the current state of the controller, the value of specific parameters, and other relevant details. The log serves as a record of the controller's activity and provides valuable insights into its operation.

int lastStep = -1;
public void Log(int step)
{
    if(lastStep != step)
    {
        using(System.IO.StreamWriter sw = System.IO.File.AppendText(@"d:\temp\log.txt"))
        {
            sw.WriteLine("TB106 step " + step.ToString());
        }
        lastStep = step;
    }
}

## Content Manager :id=contentmanager

The content manager is a method that allows you to use parameters from the simulation without defining them in the parameter controller. Below is an example of the syntax for using the content manager.

"// Controller Code

CO_Object tapis; //Pointeur vers le tapis

CO_Object cell; //Pointeur vers la cellule

public void _Init()
{
    // Get the list of products in the scene

    int count = ContentManager.Products.Count;

    //initialisation du pointeur pars l'ID de l'objet 
    tapis = ContentManager.GetObjectById(9);
    //initialisation du pointeur pars le nom de l'objet 
    cell = ContentManager.GetObjectByName("C101");
    SendMessage("Log", "Object Name " + tapis.Name);

    // Access the Disjoncteur object from the carpet object
    CO_Object disj = tapis.Parent.Child["Disjoncteur"];
}

public void _Loop()
{
   // Read the value of the cell using an enum
    bool val = (bool)cell.Data[EAttributs.DI_Valeur];
    // Write the value of the motor command using an ID
    tapis.Data[5] = !val;

    // Read the value of the "Marche" button (button name)
    bool val2 = (bool)tapis.Button["Marche"];
    // Write the value of button 1
    tapis.Button[1] = val2;

    // Read a CAB on a cell.
    if (val && cell.Colliders.Count > 0)
    {
        string V_CAB = ContentManager.GetProductById(cell.Colliders[0]).Property["CAB"];
    }
}"

<table>
        <tbody><tr>
            <th>Function</th>
            <th>Description</th>
            <th>Input/Output</th>
        </tr>
        <tr>
            <td>ContentManager.GetProductById</td>
            <td>Read A CAB on a cell.</td>
            <td>Cell/CAB.</td>
        </tr>
</tbody></table>

## CO_Object :id=co_object

CO_Object are in C# code, all the object of your simulation. To have access to thoses objects, such as cells or conveyors in order to monitor or to observe specific variables associated with those objects. You need to follow this step.

![Middle](Images/parameter_use.png ':size=500')

To use these variables, you need to add a new variable by clicking on the "add" button. Then, you can select the object and choose which variable you want to add from that object.

<video width="800" controls>
  <source src="Medias/ParameterController.mp4" type="video/mp4">
</video>

You can also create a CO_Object from your code.


## Code Example :id=codeexample

Conveyor code example

Below, you can find a code example for a conveyor. It utilizes four distinct boolean variables: TOK, ATK, DTR, and FTR. These variables are used twice, once for the head of the conveyor and once for the tail. Each boolean represents a specific state of the conveyor.

The TOK variable indicates whether the conveyor will continuously receive products or not. The DTR variable provides information that a product will soon arrive at the next conveyor. The ATR variable indicates that the conveyor is ready to receive the product. Lastly, the FTR variable signifies that the product has been processed.

The following code utilizes these eight boolean variables to process an incoming product and inform the next conveyor or industrial core that a product will soon arrive.

int g7Step = 0;
public void _Init()
{

}

public void _Loop()
{

    Btn_Step = (short)g7Step;
    TOK_Aval = Btn_Ok;
    Speed = 1000;
    if(Btn_Reset)

    {
        Avance = false;
        g7Step = 0;
    }

    switch(g7Step)
    {
        case 0:
        {
            //commandes
            Avance = false;
            //conditions
            if(DTR_Amont) {g7Step = 1; break;}
            break;
        }
        case 1:
        {
            //commandes
            Avance = Btn_Ok && DTR_Amont && AU_OK;
            ATR_Amont = Btn_Ok && AU_OK;
            //conditions
            if(Cell_In) {g7Step = 2; break;}
            break;
        }
        case 2:
        {
            //commandes
            Avance = Btn_Ok && DTR_Amont && AU_OK;
            ATR_Amont = true;
            //conditions
            if(!Cell_In) {g7Step = 3; break;}
            break;
        }
      case 3:
        {
            //commandes
            Avance = Btn_Ok && AU_OK;
            ATR_Amont = false;
            FTR_Amont = true;
            //conditions
            if(Cell_Out) {g7Step = 4; break;}
            break;
        }
      case 4:
        {
            //commandes
            Avance = false;
            DTR_Aval = true;
            //conditions
            if(ATR_Aval) {g7Step = 5; break;}
            break;
        }
      case 5:
        {
            //commandes
            Avance = ATR_Aval && AU_OK;
            //conditions
            if(FTR_Aval) {g7Step = 6; break;}
            break;
        }
      case 6:
        {
            //commandes
            Avance = false;
            DTR_Aval = false;
            FTR_Amont = false;
            //conditions
            if(true) {g7Step = 0; break;}
            break;
        }
    }
}




