# Controller Manager :id=controllermanager

- [Controller Manager](#controllermanager)
	- [Coding](#coding)
	- [Compiling](#compiling)
	- [Controller](#controller)
	- [Function](#function)
	- [Content Manager](#contentmanager)
	- [CO_Object](#co_object)
	- [Messages](#messages)
	- [Code Example](#codeexample)

# Coding :id=coding

It is possible to code in Architect, with controller. When you open a controller, by right clicking and choosing "code". You will have access to the code environment in C#. You need to know the basic of C# in order to code in Architect.

![Middle](Images/Controller.jpg ':size=500')

In this section, you will learn useful function, and specific code in Architect, not the C# basic.

# Compiling :id=compiling

You must often compile your C# code, to make sure they're is no native error in your code. Such as non defined variable, or more.

# Controller :id=controller

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

# Function :id=function


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

# Content Manager :id=contentmanager

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

# CO_Object :id=co_object

CO_Object are in C# code, all the object of your simulation. To have access to thoses objects, such as cells or conveyors in order to monitor or to observe specific variables associated with those objects. You need to follow this step.

![Middle](Images/parameter_use.png ':size=500')

To use these variables, you need to add a new variable by clicking on the "add" button. Then, you can select the object and choose which variable you want to add from that object.

<video width="800" controls>
  <source src="Medias/ParameterController.mp4" type="video/mp4">
</video>

You can also create a CO_Object from your code.

# Messages :id=messages

Controllers can send message to the scene and CO_Object.<br>
The target can be defined by setting Target property of the controller or directly use SendMEssage mathod of the CO_Object.<br>
List of messages available in controllers: 

- <b>Messages to SceneManager:</b> (no target needed) 
<table>
        <tbody><tr>
            <th>Message</th>
            <th>Description</th>
            <th>Example</th>
            <th>Information</th>
        </tr>
		<tr><td>SetSky(bool enable)</td><td>Show sky</td><td>SendMessage("SetSky", "false");</td><td></td></tr> 
		<tr><td>SetGrid(bool enable)</td><td>Show grid on floor</td><td>SendMessage("SetGrid", "false");</td><td></td></tr> 
		<tr><td>SetWalls(bool enable)</td><td>Show walls</td><td>SendMessage("SetWalls", "false");</td><td></td></tr> 
		<tr><td>SetLightEnable(bool enable)</td><td>Enable global lightening</td><td>SendMessage("SetLightEnable", "false");</td><td></td></tr> 
		<tr><td>SetBackGroundColor(string RRGGBB)</td><td>Set background color</td><td>SendMessage("SetBackGroundColor", "FFFFFF");</td><td></td></tr> 
		<tr><td>SetPhysicsGravity(string direction)</td><td>Set global gravity force</td><td>SendMessage("SetPhysicsGravity", "0,-9.81,0");</td><td></td></tr> 
		<tr><td>SetPhysicsSleepThreshold(string threshold)</td><td></td><td>SendMessage("SetPhysicsSleepThreshold", "0.01");</td><td></td></tr> 
		<tr><td>SetPhysicsContactOffset(string offset)</td><td></td><td>SendMessage("SetPhysicsContactOffset", "0.005");</td><td></td></tr> 
		<tr><td>SetFrameRate(int fps)</td><td>Force framerate</td><td>SendMessage("SetFrameRate", "100");</td><td></td></tr> 
		<tr><td>SetFixedTimeStep(float deltaTime)</td><td>Force physic framerate</td><td>SendMessage("SetFixedTimeStep", "0.02");</td><td></td></tr> 
		<tr><td>SetVSync(bool activate)</td><td>Activate VSync</td><td>SendMessage("SetVSync", "true");</td><td></td></tr> 
		<tr><td>Log(string msg)</td><td>Send message to console</td><td>SendMessage("Log", "mon message");</td><td>Write message in log</td></tr>
    </tbody></table>

- <b>Messages to conveyors:</b> 
<table>
        <tbody><tr>
            <th>Message</th>
            <th>Description</th>
            <th>Example</th>
            <th>Information</th>
        </tr>
		<tr><td>OnSetAlignmentCorrection(float align)</td><td>Set alignement from center</td><td>SendMessage("OnSetAlignmentCorrection", "0.25");</td><td>offset from center to the left</td></tr>
		<tr><td>OnSetAlignmentFactor(float factor)</td><td>Set alignement speed</td><td>SendMessage("OnSetAlignmentFactor", "0.10");</td><td>offset speed of 10% of conveyor speed (1% by default)</td></tr>
		<tr><td>OnShowHide(string visible)</td><td>Show or Hide an target object</td><td>SendMessage("OnShowHide", "true");</td><td>Show or Hide an object (true is visible)</td></tr>
    </tbody></table>


- <b>Messages to products:</b> (cells or grab can forward messages to detected products) 
<table>
        <tbody><tr>
            <th>Message</th>
            <th>Description</th>
            <th>Example</th>
            <th>Information</th>
        </tr>
		<tr><td>SetProductColor(string color)</td><td>Set product color</td><td>SendMessage("SetProductColor", "FF0000");</td><td>Color in RGB</td></tr> 
		<tr><td>SetProductCAB(string CAB)</td><td>Set product barcode</td><td>SendMessage("SetProductCAB", "00000001");</td><td>Barcode</td></tr> 
		<tr><td>SetProductModel(string model)</td><td>Set product model</td><td>SendMessage("SetProductModel", "Bandage_Double");</td><td>Model name</td></tr> 
		<tr><td>SetProductWeight(string weight)</td><td>Set product weight</td><td>SendMessage("SetProductWeight", "2500");</td><td>Weight of the product in grams</td></tr> 
		<tr><td>OnAddProductWeight(string weight)</td><td>Add or substract weight to product</td><td>SendMessage("OnAddProductWeight", "2500");</td><td>Add weight to the product (can be negative)</td></tr> 
		<tr><td>SetKinematic(bool isKinematic)</td><td>Set product as kinematic (not affected by physics)</td><td>SendMessage("SetKinematic", "true");</td><td>true if kinematic is enable (physics is disabled)</td></tr> 
		<tr><td>SetProductInfo(string attributs)</td><td>Add or modify a attribute of the product. It can be read by Readers</td><td>SendMessage("SetProductInfo", "Dest=toto");</td><td>Set a parameter of the product</td></tr> 
    </tbody></table>


- <b>Messages to objects:</b> 
<table>
        <tbody><tr>
            <th>Message</th>
            <th>Description</th>
            <th>Example</th>
            <th>Information</th>
        </tr>
		<tr><td>SetARGBColor(string color)</td><td>Set object color</td><td>SendMessage("SetARGBColor", "FF0000");</td><td>Color in RGB, alpha is optional</td></tr> 
		<tr><td>OnSetEtiquette(string text)</td><td>Add a Tag with text above the object </td><td>SendMessage("OnSetEtiquette", "Hello World!");</td><td></td></tr>  
		<tr><td>OnSetEtiquetteImage(string path)</td><td>Set tag picture</td><td>SendMessage("OnSetEtiquetteImage", "image.png");</td><td></td></tr>  
		<tr><td>OnSetEtiquetteColor(string color)</td><td>Set tag color</td><td>SendMessage("OnSetEtiquetteColor", "red");</td><td>Red or FF0000</td></tr> 
		<tr><td>StartAnimation(string Anim)</td><td>Start the animation if available</td><td>SendMessage("StartAnimation", "Open");</td><td>Execute all animations if Anim = ""</td></tr> 
		<tr><td>StartReverseAnimation(string Anim)</td><td>Start the animation in reverse if available</td><td>SendMessage("StartReverseAnimation", "Open");</td><td></td></tr> 
		<tr><td>StopAnimation(string Anim)</td><td>Stop the animation</td><td>SendMessage("StopAnimation", "Open");</td><td></td></tr> 
		<tr><td>SetAnimationSpeed(string Speed)</td><td>Set animation speed</td><td>SendMessage("SetAnimationSpeed", "2.0");</td><td></td></tr> 
    </tbody></table>


- <b>Messages to characters:</b> 
<table>
        <tbody><tr>
            <th>Message</th>
            <th>Description</th>
            <th>Example</th>
            <th>Information</th>
        </tr>
		<tr><td>OnMoveTo(string destination)</td><td>Try to find a path to destination</td><td>SendMessage("OnMoveTo", "5,0,2");</td><td>Try to find a path to destination 5,0,2</td></tr> 
		<tr><td>OnLookAt(string orientation)</td><td>Change direction to look at position</td><td>SendMessage("OnLookAt", "0,0,2.5");</td><td>Change direction to look at position 0,0,2.5</td></tr> 
		<tr><td>OnTake(string position)</td><td>Try to take a product at position</td><td>SendMessage("OnTake", "5,0,2");</td><td>Try to take a product at position 5,0,2</td></tr> 
		<tr><td>OnDrop(string position)</td><td>Try to drop a product at position</td><td>SendMessage("OnDrop", "0,0,2.5");</td><td>Try to drop a product at position 0,0,2.5</td></tr> 
    </tbody></table>
<br>

# Code Example :id=codeexample

- [TOR](#TOR)
- [Movigear](#Movigear)
- [Movidrive](#Movidrive)
- [Tempo](#Tempo)



## TOR :id=TOR

//CTRL TOR CONVEYOR

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

## Movigear :id=Movigear

//CTRL TAPIS VARIATEUR


//Movigear tapis variateur 
									  

//BB1 
//BB2 
//BB3

CO_Object CONV;		// objet convoyeur
CO_Object C_BB1;	// objet cellule
CO_Object C_BB2;	// objet cellule
CO_Object C_BB3;	// objet cellule


CO_Object BAB;
CO_Object GMF;


bool init = false;

bool debug = false;
short ACTSPD;
short ACTACC;
bool SPDOK;
int SPDSHRT;

//Use for initialization
 public void _Init()
{
 	
    GetItem( THIS.Parent,"TB", out CONV);
    
    GetItem( THIS.Parent,"BB1", out C_BB1);
    GetItem( THIS.Parent,"BB2", out C_BB2);
    GetItem( THIS.Parent,"BB3", out C_BB3);
    
    GetItem( THIS.Parent,"BAB", out BAB);
    
    GetRecurseItem( THIS.Parent,"GMF", out GMF);
    
    init = true;
    
    
    string BBType = "";
    
    BBType += C_BB1 != null? "_1" : "";
    BBType += C_BB2 != null? "_2" : "";
    BBType += C_BB3 != null? "_3" : "";
    BBType = "BB" + ((BBType == "")? "0" : BBType);
    
    SendMessage("Log", Where + " : " + BBType);
    
}
 
 
 const short cond_var_ok = 0x03;
 const short cond_var_marche = 0x80; 
 // Use as main Loop program 
 public void _Loop()
{
 	
	/**** MOVIGEAR ****/
	
    float scalef = SCL / 1000.0f;
    
    AV = ((SP[0] & cond_var_marche)!=0) && (SP[1]>0) && VAR;
    AR = ((SP[0] & cond_var_marche)!=0) && (SP[1]<0) && VAR;
    SPD = (short)Math.Abs((SP[1])*(VMAX/60.0f));
    ACTSPD = GetData<short>(CONV,EAttributs.DI_Vitesse__0_1000_);    
    SPDOK = ACTSPD!=0;
    if(AV || AR) ACC = (short)((ushort)SP[2]/5);
    else ACC =  (short)((ushort)SP[3]/5);
    ACTACC = ACC;
    //RST = ((SP[0] & 0x100) != 0); // En Option
    TSN = VAR;
    //
    //((((SP[0] & cond_var_ok)!=0)?0x07:0) | ((SP[0] & cond_var_marche)!=0)?0x10:0)

	//EP[0] = (short) ((((SP[0] & cond_var_ok)!=0)?0x10:0) | (((SP[0] & cond_var_marche)!=0)?0x07:0));
    //EP[0] = (short) ((((SP[0] & cond_var_marche)!=0)?0x10:0) | 0x07); //on a ajouté le 0x05 pour les signaux Pret et libéré du variateur (cf : Fb_MvGCtrlVar Rg1 et 2)
    EP[0] = (short) ((SPDOK?0x10:0) + 0x07); //on a ajouté le 0x05 pour les signaux Pret et libéré du variateur (cf : Fb_MvGCtrlVar Rg1 et 2)       
    EP[1] = (short) (((SP[0] & cond_var_ok)!=0)?1800:0);
    EP[2] = (short) (Defaut);
    EP[3] = 0;
    EP[4] = (short) ( (VAR?Mov_DI01:0) 
                     | (BB1?Mov_DI02:0) 
                     | (BB2?Mov_DI03:0) 
                     | (BB3?Mov_DI04:0) 
                    | 0x01);  //on a ajouté le 0x01 pour le signal DI0 du variateur (cf : Fb_MvGEtVar Rg11)
    EP[6] = (short) (((int)(COD / scalef))>>16);
    EP[7] = (short) (((int)(COD / scalef)) & 0xFFFF);
}
 
public void _Stop()
{
	init = false;
}
 
 
 
 

#region Propriete
	// convoyeur
    bool AV { set { SetData(CONV,EAttributs.DO_JOG_PLUS, value); } get {return GetData<bool>(CONV,EAttributs.DO_JOG_PLUS);}}
    bool AR { set { SetData(CONV,EAttributs.DO_JOG_MOINS, value); } get {return GetData<bool>(CONV,EAttributs.DO_JOG_MOINS);}}
    bool RST { set { SetData(CONV,EAttributs.DO_Reset, value); } get {return GetData<bool>(CONV,EAttributs.DO_Reset);}}
    short SPD { set { SetData(CONV,EAttributs.DO_Vitesse__0_1000_, value); } get {return GetData<short>(CONV,EAttributs.DO_Vitesse__0_1000_);}}
    short ACC { set { SetData(CONV,EAttributs.DO_Acceleration, value); } get {return GetData<short>(CONV,EAttributs.DO_Acceleration);}}
    Int32 COD { set { SetData(CONV,EAttributs.DI_Codeur, value); } get {return GetData<Int32>(CONV,EAttributs.DI_Codeur);}}
    
    // boutons
    bool VAR { get{ return GetButton<bool>(BAB, "Interrupteur Variateur");} }
    bool TSN { set { SetButton(BAB, 1, value);} get{ return GetButton<bool>(BAB, "Tension");} }
    Int32 SCL { get{ return GetButton<Int32>(BAB, "Rapport Codeur (mm/inc)");} }
    Int16 VMAX { get{ return GetButton<Int16>(BAB, "Vmax (m/min)");} }
    short Defaut { get{ return GetButton<short>(BAB, "Defaut");} }
    
    // cellules
    bool BB1 { get {return GetData<bool>(C_BB1, EAttributs.DI_Valeur);}}
    bool BB2 { get {return GetData<bool>(C_BB2, EAttributs.DI_Valeur);}}
    bool BB3 { get {return GetData<bool>(C_BB3, EAttributs.DI_Valeur);}}
     
    
    // a revoir GMF_KM_Num
    bool KM { get{ return GMF_KM_Num < 0? true : GetButton<bool>(GMF, GMF_KM_Num);} }
    Int16 Factor_Vitesse { get {return GetButton<Int16>(GMF, "Vitesse_Facteur");}}
#endregion
 
 
#region constantes
	const short Mov_DI00 = 0x0001;
	const short Mov_DI01 = 0x0002;
	const short Mov_DI02 = 0x0004;
	const short Mov_DI03 = 0x0008;
	const short Mov_DI04 = 0x0010;
	const short Mov_DI05 = 0x0020;
	const short Mov_DI06 = 0x0040;
	const short Mov_DI07 = 0x0080;
	const short Mov_DI08 = 0x0100;
	const short Mov_DI09 = 0x0200;
	const short Mov_DI10 = 0x0400;
	const short Mov_DI11 = 0x0800;
	const short Mov_DI12 = 0x1000;
	const short Mov_DI13 = 0x2000;
	const short Mov_DI14 = 0x4000;
	//const short Mov_DI15 = 0x8000; passage en int ou ushort necessaire
#endregion



## Movidrive :id=Movidrive

//CTRL NAVETTE

//AS1 - Movidrive


CO_Object BAB;
CO_Object TR;
CO_Object GMF;
CO_Object GRABBER;
bool init = false;

bool retKA1YA1; // 05/04/2022

//Use for initialization 
 public void _Init()
{
    //SendMessage("Log", "CP Start");
    
    GetItem( THIS.Parent.Parent,"TR", out TR);
    GetItem( THIS.Parent,"BAB", out BAB);
    GetItem( THIS.Parent,"GRABBER", out GRABBER);
    //GetRecurseItem( THIS.Parent,"GMF", out GMF);
    
    init = true;
}
 // Use as main Loop program 
 public void _Loop()
{
    if(! init) _Init();
    

    GRAB = (AV || AR);

    DROP = (!AV && !AR);
  
    EKAVER = KAVER;    
    
    bool varOk = VAROK /*&& KM*/;
    AV = (SP[1] > 0) && (SP[0] & 0x80)==0x80 && varOk;
    AR =  (SP[1] < 0) && (SP[0] & 0x80)==0x80 && varOk;
    SPD = (short) Math.Abs((SP[1]));
    
    EP[0] = (short)((VAROK?0x01 : 0) | (VAROK?0x02 : 0) | (VAROK?0x04 : 0) | ((AV || AR)?0x10 : 0) );
    EP[1] = ISPD;
    //EP[2] = 0;	
    byte[] bytes = BitConverter.GetBytes((ushort)(200*0x100));

    EP[2] = BitConverter.ToInt16(bytes, 0);
    
    // 05/04/2022 : relai ouverture bloqueur AS1  
//    if(KA1YA1 != retKA1YA1)
//    {
//        SQ11AS1 = KA1YA1S1 = KA1YA1;
//    }
//    retKA1YA1 = KA1YA1;
    
}


public void _Stop()
{
    init = false;
}


#region Propriete

    bool AV { set { SetData(TR,EAttributs.DO_Jog_Forward, value); } get {return GetData<bool>(TR,EAttributs.DO_Jog_Forward);}}
    bool AR { set { SetData(TR,EAttributs.DO_Jog_Backward, value); } get {return GetData<bool>(TR,EAttributs.DO_Jog_Backward);}}
    short SPD { set { SetData(TR,EAttributs.DO_Speed_0_1000, value); } get {return GetData<short>(TR,EAttributs.DO_Speed_0_1000);}}
    Int32 COD { get {return GetData<Int32>(TR,EAttributs.DI_Encoder);}}
    short ISPD { get {return GetData<short>(TR,EAttributs.DI_Speed_0_1000);}}
   
    bool POSOK { get {return GetData<bool>(TR,EAttributs.DI_Position_OK);}}
    
    Int32 scale { get{ return GetButton<Int32>(BAB, "Rapport Codeur (mm/inc)");} }
    bool VAROK { get{ return GetButton<bool>(BAB, "Interrupteur Variateur");} }
    bool TSN { set { SetButton(BAB, "Tension", value);} get{ return GetButton<bool>(BAB, "Tension");} }
    Int16 VMAX { get{ return GetButton<Int16>(BAB, "Vmax (m/min)");} }
    
    bool GRAB { set { if (GRABBER!=null) GRABBER.SetData(EAttributs.DO_Take, value); } get {return (GRABBER!=null)? GRABBER.GetData<bool>(EAttributs.DO_Take) : false;}}    
    bool DROP { set { if (GRABBER!=null) GRABBER.SetData(EAttributs.DO_Drop, value); } get {return (GRABBER!=null)? GRABBER.GetData<bool>(EAttributs.DO_Drop) : false;}}        
    Int16 VGRAB { set { if (GRABBER!=null) GRABBER.SetData(EAttributs.DI_Speed_0_1000, value); } get {return  (GRABBER!=null)? GRABBER.GetData<Int16>(EAttributs.DI_Speed_0_1000) : (Int16)0;}}
    
    // a revoir GMF_KM_Num
    //bool KM { get{ return GMF_KM_Num < 0? true : GetButton<bool>(GMF, GMF_KM_Num);} }
    //Int16 Factor_Vitesse { get {return GetButton<Int16>(GMF, "Vitesse_Facteur");}}

    
    
    // 05/04/2022 : relai ouverture bloqueur AS1    
//    bool KA1YA1 { get {return GetButton<bool>(BAB, 8);}  }
//   bool KA1YA1S1 { set {SetButton(BAB, 9, value);} }
//    bool SQ11AS1 { set {SetButton(BAB, 10, value);} }

    
    
#endregion

## Tempo :id=Tempo

//CTRL TEMPO BIELE

CO_Object BAB;
CO_Object TP;

DateTime tempo;

bool init = false;
int g7Step = 0;
//Use for initialization 
 public void _Init()
{
    //SendMessage("Log", "CP Start");
    
    THIS.Parent.GetItem("TP", out TP);   
    init = true;
}

 // Use as main Loop program 
 public void _Loop()
{
    if(! init) _Init();
    
    switch(g7Step)
    {
    		case 0 :
    		AV = SKMELEVC;
    		AR = false;
    		if(Hi) g7Step = 1;
    		break;
    		
    		case 1 :
    		tempo = DateTime.Now;
    		g7Step = 2;
    		break;
    		
    		case 2 :
    		if ((DateTime.Now - tempo).TotalMilliseconds > 1000)
    		{
                    g7Step = 3;
            }
    		break;
    		
    		case 3 :
    		AV = false;
    		AR = SKMELEVC;
    		if(Lo) g7Step = 4;
    		break;
    		
    		case 4 :
    		tempo = DateTime.Now;
    		g7Step = 5;
    		break;

    		case 5 :
    		if ((DateTime.Now - tempo).TotalMilliseconds > 1000)
    		{
                    g7Step = 0;
            }
    		break;
    		   
    }
    
    KMELEVC = !SKMELEVC;
    }


 public void _Stop()
 {
    init = false;
 }


#region Propriete
  bool AV { set { if (TP!=null) TP.SetData(EAttributs.DO_Jog_Forward, value); } get {return  (TP!=null)? TP.GetData<bool>(EAttributs.DO_Jog_Forward) : false;}}
  bool AR { set { if (TP!=null) TP.SetData(EAttributs.DO_Jog_Backward, value); } get {return (TP!=null)? TP.GetData<bool>(EAttributs.DO_Jog_Backward) : false;}}
  
//  bool High { set { if (TP!=null) TP.SetData(EAttributs.DI_High, value); } get {return  (TP!=null)? TP.GetData<bool>(EAttributs.DI_High) : false;}}
//  bool Low { set { if (TP!=null) TP.SetData(EAttributs.DI_Low, value); } get {return (TP!=null)? TP.GetData<bool>(EAttributs.DI_Low) : false;}}
   

  Int32 Encoder { set { if (TP!=null) TP.SetData(EAttributs.DI_Encoder, value); } get {return  (TP!=null)? TP.GetData<Int32>(EAttributs.DI_Encoder) : (Int32)0;}}
    
  bool Hi { set { if (TP!=null) TP.SetData(EAttributs.DI_High, value); } get {return  (TP!=null)? TP.GetData<bool>(EAttributs.DI_High) : false;}}
  bool Lo { set { if (TP!=null) TP.SetData(EAttributs.DI_Low, value); } get {return (TP!=null)? TP.GetData<bool>(EAttributs.DI_Low) : false;}}
   
            
#endregion