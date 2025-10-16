# Button Manager :id=buttonmanager

Buttons are really useful. it enable to monitor manually some data, without an automate or to forced a data. They are most of the time use, as emergency buttons, or direction levers. Every object can have button.

<video width="800" controls>
  <source src="Medias/Button.mp4" type="video/mp4">
</video>

<table>
    <tbody>
        <tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        <tr>
        </tr><tr>
            <td>Description</td>
            <td>you can write the name or the utility of your button.</td>
        </tr>
        <tr>
            <td>Value</td>
            <td>The value that can you want to settle with your button. You can push, toggle or settle your button.</td>
        </tr>
        <tr>
            <td>Types</td>
            <td>You can choose the types of your buttons among many of them. they will be listed just below.</td>
        </tr>
        <tr>
            <td>Init Value</td>
            <td>Choose what will be the first value for your button.</td>
        </tr>
        <tr>
            <td>Adress</td>
            <td>You can give an address to find your buttons of the data monitor.</td>
        </tr>
        <tr>
            <td>Color</td>
            <td>you can choose the light color of the button. (only usable in button_light mode)</td>
        </tr>
        <tr>
            <td>True Status</td>
            <td>Inverse for PLC, true and false value, in order to do not be dissonant with PLC.</td>
        </tr>
    </tbody>
</table>

<table>
    <tbody>
        <tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
        <tr>
        </tr><tr>
            <td>bouton_toggle</td>
            <td>It is a on/off button.</td>
        </tr>
        <tr>
            <td>bouton_push</td>
            <td>It is a push button, click once to turn it on.</td>
        </tr>
        <tr>
            <td>bouton_int_16</td>
            <td>Set a data to an integer in 16bits, from 0 to 65 536.</td>
        </tr>
        <tr>
            <td>bouton_light</td>
            <td>Boolean which light on if the value are on.</td>
        </tr>
        <tr>
            <td>bouton_int16_read</td>
            <td>Read the integer's data.</td>
        </tr>
        <tr>
            <td>bouton_radio</td>
            <td>Deactivate the selected object or group.</td>
        </tr>
        <tr>
            <td>bouton_title</td>
            <td>Hide the selected object or group. This is only visual.</td>
        </tr>
        <tr>
            <td>bouton_int32</td>
            <td>Set a data to an integer, from 0 to 4 294 967 295.</td>
        </tr>
        <tr>
            <td>bouton_int32_read</td>
            <td>Read the integer's data.</td>
        </tr>
        <tr>
            <td>bouton_text</td>
            <td>Set a text to an integer.</td>
        </tr>
        <tr>
            <td>bouton_text_read</td>
            <td>Read the text's data.</td>
        </tr>
    </tbody>
</table>

When you had a button in the project, the button's data can be see in the data monitor. You can monitor a button box, in the data monitor as well.


<video width="800" controls>
  <source src="Medias/Buttonbox.mp4" type="video/mp4">
</video>

All the configuration of a button box can be done in the configuration file.

