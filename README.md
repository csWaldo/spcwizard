Static Prop Combine Wizard
=====

![alt text](https://i.imgur.com/PpVHFNj.png "UI")

## About
This tool aims to simplify and partially automate the process of setting up static prop combine (SPC) for Counter-Strike Global Offensive.
The wizard allows to you to easily generate or edit rules for SPC and will automatically generate the required stub .qc files.
 
**IMPORTANT:** To use SPC you must have access to the models source files as well as a basic understanding of how models are compiled for the source engine!

## Setting up Static Prop Combine
### Models & Model Source Files
In order to create the combined models SPC needs access to the models source files.

**IMPORTANT:** SPC will only look for model source files inside **../steamapps/common/content/csgo**

* Every model you intend to use with SPC must have its source files somewhere in this path.
E.g. you might store the source files for *mymodel.mdl* in **../steamapps/common/content/csgo/mymap/mymodel**

**IMPORTANT:** You must compile your models (again) after moving their source files to this folder!

* SPC will read the path to each models source files directly from the .mdl. The models must therefor be compiled from inside the content folder so SPC can find them.

If you are using an addon such as SourceOps or WallWorm I would recommend setting your **modelsrc** folder to **../steamapps/common/content/csgo/modelsrc**.

### spcombinerules.txt
This file is located in ../csgo/scripts/hammer/spcombinerules and may contain any number of rules used by SPC to combine models.

Each rule represents a set of combineable models and contains:

key | use
--- | ---
name | used to name the combined model
cluster size | max. number of models that can be combined into one
distance limit | max. distance between models to be combined (origin to origin, hammer units)
peers | list of models that can combined with each other
stub .qc| path to the stub .qc used to compile the combined model

### .qc stubs
Used by SPC to compile the combined model.

Each rule has its own stub .qc which **may** contain:

key | use
--- | ---
$cdmaterials | material folder for the combined model
$surfaceprop | surface property for the combined model
$texturegroup | list of skins used by the combined model

### Static Prop Combine Wizard
The SPC wizard serves as a GUI for creating and editing the spcombinerules.txt as well as the .qc stubs.

#### Install & Setup
* Download & unpack the repository
* Run spcwizard.exe
* Press **browse** and browse to your **../Counter-Strike Global Offensive/csgo** folder

You should now see this:
![alt text](https://i.imgur.com/bK3tCTF.png "UI")
 
