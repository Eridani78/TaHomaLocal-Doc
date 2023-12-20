# **TaHomaLocal** Plugin
<img src="/docs/assets/images/TaHomaLocal-Image.png" alt="" style="height: 40%; width:40%;"/>
<img src="/TaHomaLocal-Doc/assets/images/TaHomaLocal-Image.png" alt="TaHomaLocal logo" style="height: 40%; width:40%;"/>

## Presentation
The TaHomaLocal plugin is intended to enable an interface between Jeedom and a Somfy TaHoma box (or eligible equivalent Somfy box) on which the Somfy local API has been activated.

As a reminder, an API (Application Programming Interface) allows connection between software applications or services in order to exchange data and functionalities.
Once installed and properly configured, the TaHomaLocal plugin then permits, via the local network to which the box is connected (LAN), the sending of commands and the reading of data from devices coupled to the box and controlled by the latter. The sending and receiving of data is then no longer transmitted and received via the Internet and via a Somfy server. The exchanges remain internal to the local network.
This results in 'cloudless' operation which is independent from the Internet and provide for compatible commands, an almost instantaneous status feedback.


## Somfy/TaHoma ecosystem
The Somfy TaHoma ecosystem currently includes numerous partners and is likely to continue to expand and evolve.
This means that a TaHoma box can interface and control many devices that are very different from each other. Currently the Somfy ecosystem offers the control of devices such as opening (roller shutters, doors, blinds), alarm systems, heating systems and air conditioning, ...
The lack of documentation from Somfy on the device commands makes the syntax of these operations particularly difficult to anticipate and to implement in a plugin.
In order to best adapt to such a diversity of potential commands or data, two operating modes of the plugin have been implemented.

Mode **Smart** Mode

This first mode creates the main commands for a given equipment.
The choice of the created commands comes from a “Components” database which is enriched as the plugin is deployed.
For this, the TaHomaLocal plugin integrates a learning method. This method must allow, as far as possible, adaptation of the plugin to the different devices encountered.
This adaptation is not automatic and may require the transmission by the user of data recorded during plugin initialization.
During the plugin initialization phase, and if the case arises, unknown equipments will be listed in the resulting table indicating to the user that these new devices are not included in the database.
It will then be up to the user to transmit via MP, the data files concerning devices not yet known to the plugin so that they can be taken into account and integrated into the plugin component database.
No sensitive personal data other than component descriptions is transmitted via this link.

**Full** Mode

This second mode creates, without filters, all the available commands for a given equipment.
This is a mode that must be chosen with care because it creates operational commands but also "Admin" type commands and "Settings" type commands.
Using some of these commands could be inappropriate or can modify some settings made during the installation of the equipment, often via proprietary applications.
It has also to be noticed, that the parameter syntaxes needed to use certain commands may not be known by the plugin.


## Initialization and implementation steps of the **TaHomaLocal** plugin

### Step 1 – Enabling local API
Activation of the local API must be carried out by the user of the TaHoma box
First connect to the Somfy website and navigate to the `My Account` menu. Find the different available options for your TaHoma box and activate `Developer Mode`.
Activating this mode will enable a local API on your TaHoma box.

Not all Somfy box models accept the activation of a “Developer Mode”. It is therefore up to the user to ensure that their Somfy box model is compatible with this mode.
Please note that the general conditions and Somfy rules for "Developer mode" also apply to the **TaHomaLocal** plugin.

After "Developer Mode" activation, we recommend to perform a RESET of the Somfy box to ensure local API activation.
For a Somfy box, how to perform a RESET can be found on the Internet.

Step 2 - Installing the plugin

Once installed, carry out the following operations: 
- In Status: Activate 
- In Dependencies: Launch


### Step 3 - Configuration / Plugin Configuration
#### Box model
Select your Somfy box model.

#### User Id & User Password
Configuring the plugin requires the user to enter their Somfy account login credentials (Email & Password).

#### Plugin Mode
Select plugin mode.
- Smart mode is the default plugin mode.
- Full is an advanced mode (see description above).

#### IPv4 Address (optionnal)
This field should be kept empty and should only be used temporarily in the event of a problem accessing the box (DNS problem for example).

#### Socket Port (optionnal)
The plugin uses a default value for this data and in the majority of cases the user will not have to use this field.
To avoid the possibility of a collision with the port used by another plugin, this field can be used to change the port number used by the **TaHomaLocal** plugin.

#### Daemon
Do not start the Daemon manually.
This will start on its own and the plugin will be operational after 1 to 2 minutes.
During this Daemon synchronisation phase, certain error messages may appear and must be ignored.

#### Cron
For the plugin to function correctly, the cron "cron" must be kept 'enabled'.
<img src="/docs/assets/images/TaHomaLocal-Plugin_configuration-Fonctionnality-cron.png" alt="" style="height: 50%; width:50%;"/>
<img src="/TaHomaLocal-Doc/assets/images/TaHomaLocal-Plugin_configuration-Fonctionnality-cron.png" alt="Image TaHomaLocal-Plugin_configuration-Fonctionnality-cron" style="height: 50%; width:50%;"/>

### Step 4 - Discovery of gateways / Discovery of compatible boxes on the network
When this action is launched, the plugin scans the network in search of one or more Somfy boxes (or compatible) which are connected to the LAN.
The boxes with the local API enbled are identified in the resulting table.
In the case where several boxes are recognized, the TaHomaLocal plugin allows the user to select the box which will be declared an (active) gateway for the plugin.
Select the active gateway by clicking on the point, then exit with `Save`.

### Step 5 - API Authentication / Authentication - Obtaining a Token
⚠ This step requires an internet access.

In order to use the box's local API, it is necessary to authenticate exchanges with it.
This security imposed by Somfy is achieved by obtaining an authentication Token from the Somfy server during the initialization phase.
Once obtained, this Token saved at the box and plugin levels is kept and used to authenticate exchanges on the local network.
Renewing or obtaining a new Token may, under certain circumstances, be necessary, in the event of a Reset of the box for example.
The Token request can only be made after a box has been selected as (active) gateway.
Even if only one Token is necessary, the Somfy API provides the possibility of obtaining several.
The TaHomaLocal plugin integrates a functionality allowing one or more Token(s) to be obtained and the active Token to be selected.
The fields "Token Label" and "Token Scope" are optional and can be leaved blank.

### Step 6 - Import equipment
When launching this action, the plugin imports the equipment declared in the box and creates the commands associated with each equipment.

During this operation and if equipment are listed under **Unknown equipment found**, this means that these equipment are not integrated yet in the plugin database.
Please perform the following operation :


1. Using the Jeedom File Editor, navigate to the folder
> ```
> html/plugins/TaHomaLocal/data/components/undefined
> ```

New unknown equipement are present in this folder.

2. Select the `undefined` folder, then right click on the mouse **Create archive ZIP**, rename archive adding `.txt`.

3. Function **Upload files** (up arrow) to your computer.

4. Send the file to the plugin author (** important** with PM for confidentiality aspects).

Equipemnt will be added to the plugin database as soon as possible.

### Step 7 - Use
The plugin configuration is complete. The available commands can then be integrated, if necessary, renamed and used within Jeedom.

## Mobile and other apps
To the extent that they are not installed under Jeedom, the installation and use of the **TaHomaLocal** plugin has no impact and does not prevent the use of dedicated applications provided by Somfy or by its partners with the ecosystem devices (apps on mobile phones for example).

## List of equipment registered in the Database
The list of equipment recognized by the plugin is kept up to date in the plugin changelog.
In this list, components are described according to their generic Somfy classification and not by their commercial brand or model.

## Routines
Routine management is, until now, not supported by the Somfy local API.

## Stopping the Daemon
Even if this operation is not recommended, the user can decide to stop the Daemon (in the Plugin Configuration panel).
In this case, the Daemon will restart automatically after a plugin resynchronization time of up to 1 minutes.
During this time, some commands may no longer be operational.

## Evolution of Somfy policy
The Jeedom entity, as well as the designer of the TaHomaLocal plugin, cannot, under any circumstances and in any way, be held responsible for a change in Somfy policy which would lead to:
-	a significant change in the API rendering the plugin inoperable, or
-	removal of the access, by Somfy, of the local API as it was defined when designing the plugin.
