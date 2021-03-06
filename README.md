Static Prop Combine Wizard
=====

![alt text](https://i.imgur.com/PpVHFNj.png "UI")

## About
This tool aims to simplify and partially automate the process of setting up static prop combine (SPC) for Counter-Strike Global Offensive.
The wizard allows to you to easily generate or edit rules for SPC and will automatically generate the required stub .qc files.
 
**IMPORTANT:** To use SPC you must have access to the models source files as well as a basic understanding of how models are compiled for the source engine!

## Setting up Static Prop Combine
### Models & Model Source Files
In order to create the combined models SPC needs access to the models source files. The source files have the following limitations:
* only the first $body is recognized
* $bodygroup is not recognized
* $model is not recognized
* $appendsource and $addconvexsrc are not recognized
* You can only use $upaxis Z or Y.

**IMPORTANT:** SPC will only look for model source files inside **../steamapps/common/content/csgo**

* Every model you intend to use with SPC must have its source files somewhere in this path.
E.g. you might store the source files for *mymodel.mdl* in **../steamapps/common/content/csgo/mymap/mymodel**

**IMPORTANT:** You must compile your models (again) after moving their source files to this folder!

* SPC will read the path to each models source files directly from the .mdl. The models must therefor be compiled from inside the content folder so SPC can find them.

If you are using an addon such as SourceOps or WallWorm I would recommend setting your **modelsrc** folder to **../steamapps/common/content/csgo/modelsrc**.

### spcombinerules.txt
This file is located in ../csgo/scripts/hammer/spcombinerules and may contain any number of rules used by SPC to combine models.

Each rule represents a set of combineable models and has a:

key | use
--- | ---
name | used to name the combined model
cluster size | max. number of models that can be combined into one
distance limit | max. distance between models to be combined (origin to origin, hammer units)
peers | list of models that can combined with each other
stub .qc| path to the stub .qc used to compile the combined model

### stub .qcs
Used by SPC to compile the combined model.

Each rule has its own stub .qc which **may** contain:

key | use
--- | ---
$cdmaterials | material folder for the combined model
$surfaceprop | surface property for the combined model
$texturegroup | list of skins used by the combined model

### Static Prop Combine Wizard
The SPC wizard serves as a GUI for creating and editing the spcombinerules.txt as well as the stub .qcs.

#### Install & Setup
* Download & unpack the repository
* Run spcwizard.exe
* Press **browse** and browse to your **../Counter-Strike Global Offensive/csgo** folder

You should now see this:
![alt text](https://i.imgur.com/bK3tCTF.png "UI")

#### Use
* add and remove rules with the respective buttons
* load rules from a spcombinerules.txt

   this will discard your current rules
* save rules to a spcombinerules.txt

   this will also generate all neccessary stub .qcs

Selecting a rule will reveil its properties:
![alt text](https://i.imgur.com/iqWZ9HH.png "UI")
At the top you can see and edit the selected rules name.
The left side shows the rule and its settings. The right side shows the associated stub .qc and its settings.

Add models to the rule by clicking *Add* and selecting one or multiple .qc files from your model source files in **content/csgo**.

The stub .qc settings are populated by the first model you add to a rule but you can also edit them manually.

---

When you are happy with your rules, press save to write a spcombinerules.txt and all its associated stub .qcs.
You can give the rule file any name but SPC will **only** read the file called **spcombinerules.txt**.
It might also be a good idea to keep a backup of your rule file as it may get overwritten when the game updates.

### Running Static Prop Combine
Add **-staticpropcombine** to **vbsp.exe** to enable SPC. The combined models will automatically be packed into the compiled .bsp.

You can add more parameters to change how SPC behaves. Here you can read more about them and SPC in general:
* https://developer.valvesoftware.com/wiki/Static_Prop_Combine
* https://www.mapcore.org/articles/tutorials/static-prop-combine-in-csgo-r111/
