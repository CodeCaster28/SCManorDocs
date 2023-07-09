# SCManorDocs

The idea behind this repo is to allow users to contribute to Sven Co-op Manor Entity Guide documentation.
Sven Co-op Manor Entity Guide is using Sven Co-op FGD and documentation files to generate webpages you see in svenmanor.com.
To contribute, fork this repo, make your changes and create a Pull Request. After accepted, I upload changes to svenmanor.com (unfortunately there is no automation for this).

If changing for future Sven Co-op version (release candidate) please use branch named after game version. E.g. for 5.26 you should use branch "rc5.26".

Two folders are present in this repo: BaseClasses and Entities. Both contains .json files. 

Each file inside Entities folder represents sven co-op entity, while BaseClasses contains all base classes that are shared between some of the entities.
The structure is similar to FGD, each entity description consist of one file from Entities folder and files from BaseClasses based on what are base classes of this entity.

Check wiki for documentation:
https://github.com/CodeCaster28/SCManorDocs/wiki

## Changing description of entities
Every entity inside Entities/ folder have description on op of file:
```
{
  "Classname": "trigger_push",
  "Description": "A simple brush entity for affecting entities inside it with acceleration towards a certain direction.",
  (...)
```
Just edit text inside "Description" and you're good to go! For now, images are not supported (tehy need to be uploaded separately).

## Changing description of entity keyvalues
### Example 1
Func_plat entity FGD structure looks like this:
```
@SolidClass base(Targetname, Global, RenderFields, PlatSounds, BasePlat, ZHLT) = func_plat : "Elevator"
[
	spawnflags(Flags) =
	[
		1: "Toggle" : 0
	]
	height(integer) : "Travel altitude (can be negative)" : 0
	speed(integer) : "Speed" : 50
	_minlight(string) : "Minimum light level"
]
```

This mean .jsons that describes this entity keyvalues are: 
* Entities/func_plat.json  	(this entity's unique keyvalues)
* BaseClasses/Targetname.json	(Targetname keyvalues that is used by many entities)
* BaseClasses/Global.json 	(Global keyvalues)
* BaseClasses/RenderFields.json	(RenderFields keyvalues)
* BaseClasses/PlatSounds.json	(PlatSounds keyvalues)
* BaseClasses/BasePlat.json	(BasePlat keyvalues)
* BaseClasses/ZHLT.json		(ZHLT keyvalues)

Considering that you want to change description of "Speed" keyvalue:

<img src="https://github.com/CodeCaster28/SCManorDocs/assets/16106194/7d26c4f7-0a0a-4571-9908-c47908226169.png" width="350">

You should edit Entities/func_plat.json and change keyDescription value under "keyName": "speed":
```
    {
      "keyName": "speed",
      "keyDescription": "Movement-speed in units per second.",
      "keyChoices": []
    },
```


Final website generated with these .jsons can be seen here: https://www.svenmanor.com/entity-guide/func_plat

### Example 2
Let's stay with func_plat example. Consider changing "Fire On Stop" keyvalue description. You won't find this keyvalue inside Entities/func_plat.json because it's inherited from base classes.
In this case from BasePlat which inherit further from StartStopable:
```
    {
      "keyName": "fireonstop",
      "keyDescription": "Entity to trigger when {{ entname }} stops moving. Trigger use-type can be specified below.",
      "keyChoices": []
    },
```
Also note that "Fire On Stop" on website is really "fireonstop" in .json file. 
This is because .json uses original key name, while website displays "nice" names picked from FGD (same as those used by Smart Edit Modes in Hammer Editor).
```
fireonstop(string) : "Fire On Stop"
```
Because of this you can't change names of keyvalues inside entity guide. They are always the same as these from FGD.

More info in wiki:
https://github.com/CodeCaster28/SCManorDocs/wiki


