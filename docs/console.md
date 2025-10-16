# Console :id=console

The console in Architect functions similarly to a traditional coding environment console. It displays various information about your simulation, such as the current state, any errors that may have occurred, the text you write along with your code, the compilation status of your controllers, and more.

![Middle](Images/console.png ':size=2000')

>Toolbar

<table>
        <tbody><tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        
            <tr><td>Clear</td>
            <td>Clear the console</td>
        </tr>
        <tr>
            <td>Collapse</td>
            <td>Summarize all the messages together if they said the same information.</td>
        </tr>
            <tr><td>Clear on Play</td>
            <td>At each run of the simulation, the console will be clear</td>
        </tr>
            <tr><td>Scroll Top</td>
            <td>Scroll to the top of the console</td>
        </tr>
            <tr><td>Scroll Bottom</td>
            <td>Scroll to the bottom of the console</td>
        </tr>
            <tr><td>Filter</td>
            <td>A filter, in order to find specific lines in the console</td>
        </tr>
</tbody></table>

>Messages

This is the answer from the console, for the status of this line. It can answer "Compile OK" or an error.

<table>
        <tbody><tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>Time</td>
            <td>This indicated the time when occur line</td>
        </tr>
        
            <tr><td>Level</td>
            <td>Information message are in Red. Trace in Blue, are the path line that the console read. Debug in White, are the lines where some bugs can appears. Error are in Red.</td>
        </tr>
        
            <tr><td>Message</td>
            <td>This answer from the console, for the status of this line. It can answer "Compile OK" or an error.</td>
        </tr>
</tbody></table>


>Level

All the information have different types of importance levels, with a color hierarchy.

<table>
        <tbody><tr>
            <th>Level</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>Info in green</td>
            <td>Information link to your project</td>
        </tr>
            <tr><td>Trace in blue</td>
            <td>Trace all code lines from the software, such as controller, functions and more.</td>
        </tr>
            <tr><td>Warning in yellow</td>
            <td>Warn you that an minor has occurred, without crash the simulation.</td>
        </tr>
            <tr><td>Error in red</td>
            <td>Warn you that a fatal error has occured, and need to be fixes as soon as possible.</td>
        </tr>
</tbody></table>

>File

You can have access to the log of the console at anytime, by the Top Bar, with Tools>Open console files.

![Middle](Images/consolefiles.png ':size=2000')


In this example of console file, we can observe that first of all, my project was launch successfully, then the simulation tried to connect itself to a PLC each time in turn Run mode on. It fails because, no PLC was connected, but do not crash the simulation.
