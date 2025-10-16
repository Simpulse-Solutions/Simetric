# Communication  :id=communication

The communication window is use to make the link between the Architect's I/O, and the PLC. 

![Middle](Images/First_scheme.png ':size=500')

Before testing your simulation with a PLC, make sure that your simulation works without it.

To make the good communication you need to follow those four step :

- [Communication](#communication)
	- [Tagging](#tagging)
	- [Aliasing](#aliasing)
	- [Link](#link)
	- [Play](#play)
	- [Window](#window)



## Tagging :id=tagging

A Tag is the address for the I/O in the simulation, and Tagging is the action to give a Tag to an I/O.

>Adding a PLC

To add a new PLC to the simulation, you just have to click on the "+" button, and choose your PLC.

![Middle](Images/Arrow.png ':size=500')

>Attaching a PLC

You can attach a I/O to your PLC more easily by using the Alias_Element from the "Inspector" window. It allow you to give a name at all I/O from this group, in order to find them directly. 

Then with the "Connection_Id", you need to link the groups with the PLC that you have create earlier in the "Communication" Window.

>Tagging a PLC

To tag an I/O, you can just write the tag you want, in the Data monitor, in the #Tag column. It will directly impact the full tag of the I/O, that is the combination of the Alias_element of the parent groups, and the I/O tag.


## Aliasing :id=aliasing

>Manually

You are able to aliasing your tag, by filling up the address column in the communication windows, with the corresponding address in your PLC.

>Automatically

You can also make the aliasing automatically, with a .csv file, by excel.

## Link :id=link

In order to link correctly Architect software with a PLC, you need to use a link software.

It exist three main software, IESA Link, KEP and RSLink.

![Middle](Images/IESA_Link.png ':size=500')

To establish a connection between IESA Link Client and Architect, you need to ensure that they are configured with the same IP address and path. The IP address corresponds to your computer's standard IP address, while the path refers to the slot number of your CPU. By matching these settings, you can successfully link IESA Link Client with Architect.

Once you have entered the IP and Path information, you can select the specific PLC you are using in IESA Link Client. This allows you to perform read and write operations on tags associated with the PLC. To access a particular tag, you need to provide its address, which will enable you to interact with it.


## Play :id=play

After Tagging your I/O, Aliasing correctly and link Architect with your PLC, you can now turn on the Run mode, and see your simulation in action. 


## Window :id=window

The communication window serves as the interface between Architect and your automate. It displays the status of each data element in your simulation, including its address, status, alias, and more. It will create a .alias file at the root of the project.

![Middle](Images/WindowController.png ':size=500')

>Top bar

<table>
        <tbody><tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>+</td>
            <td>Add a New automate</td>
        </tr>
        <tr>
            <td>PLC Type</td>
            <td>Choose your type of PLC.</td>
        </tr>
        <tr>
            <td>IP</td>
            <td>Write the IP of your PLC.</td>
        </tr>
        <tr>
            <td>Path</td>
            <td>Write the path of your PLC.</td>
        </tr>
        <tr>
            <td>Scan Rate</td>
            <td>Choose the scan rate for the PLC.</td>
        </tr>
        <tr>
            <td>IsConnected</td>
            <td>Show if the PLC is connected.</td>
        </tr>
        <tr>
            <td>Connect at Run</td>
            <td>Auto connect in Run Mode.</td>
        </tr>
        <tr>
            <td>Connect to Excel</td>
            <td>Address all tag with Excel.</td>
        </tr>
</tbody></table>

>Tab

<table>
        <tbody><tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>Address</td>
            <td>PLC Address for the I/O</td>
        </tr>
        <tr>
            <td>Alias</td>
            <td>name of the I/O.</td>
        </tr>
        <tr>
            <td>Status</td>
            <td>Show the status of the I/O.</td>
        </tr>
        <tr>
            <td>TrueStatus</td>
            <td>show the state of the I/O see from the PLC.</td>
        </tr>
        <tr>
            <td>InitValue</td>
            <td>Iniatilization of the first I/O value.</td>
        </tr>
        <tr>
            <td>Data_ID</td>
            <td>.</td>
        </tr>
</tbody></table>

>PLC Type

Architect supports various types of PLCs, and to establish a connection between the PLC and Architect, you need specific software that acts as a bridge between them. There are three different software options available: IESA Link Client, KEPServer, and RS_Linx. These software tools facilitate the seamless integration and communication between your PLC and Architect.

Most of the PLC types listed in Architect are compatible with IESA Link Client for communication. However, the last two PLC types, namely "OPC_RS_Linx" and "OPC_KEP_VS", require specific software for integration. "OPC_RS_Linx" is compatible with RS_Linx, while "OPC_KEP_VS" works with KEPServer for establishing the connection between the PLC and Architect.

<table>
        <tbody><tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>RS_Micro</td>
            <td>.</td>
        </tr>
        <tr>
            <td>RS_PLC</td>
            <td>.</td>
        </tr>
        <tr>
            <td>RS_MicroPLCCNET</td>
            <td>.</td>
        </tr>
        <tr>
            <td>RS_SLC</td>
            <td>.</td>
        </tr>
        <tr>
            <td>S7_200</td>
            <td>.</td>
        </tr>
        <tr>
            <td>S7_300</td>
            <td>.</td>
        </tr>
        <tr>
            <td>S7_400</td>
            <td>.</td>
        </tr>
        <tr>
            <td>S7_1200</td>
            <td>.</td>
        </tr>
        <tr>
            <td>MB_TCP</td>
            <td>.</td>
        </tr>
        <tr>
            <td>MB_SOE</td>
            <td>.</td>
        </tr>
        <tr>
            <td>ADS_TWINCAT2</td>
            <td>.</td>
        </tr>
        <tr>
            <td>ADS_TWINCAT3</td>
            <td>.</td>
        </tr>
        <tr>
            <td>OPC_RS_LINX</td>
            <td>.</td>
        </tr>
        <tr>
            <td>OPC_KEP_V5</td>
            <td>.</td>
        </tr>
</tbody></table>

Almost all of the PLC listed here, need an IP and a Path. Each PLC have a different way to written the PLC, but most of them are the number of the slot use in the CPU.

- Siemens : Use the backplane
- S7_200 to S7_1200 : Use 0.1 or 0.2
- Twincat : Use and number with 6 dot (.), 





