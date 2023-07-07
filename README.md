# SCManorDocs

The idea behind this repo is to allow users to contribute to Sven Co-op Manor Entity Guide documentation.
Sven Co-op Manor Entity Guide is using Sven Co-op FGD and documentation files to generate webpages you see in svenmanor.com.

Two folders are present in this repo: BaseClasses and Entities. Both contains .json files. 

Each file inside Entities folder represents sven co-op entity, while BaseClasses contains all base classes that are shared between some of the entities.
The structure is similar to FGD, each entity description consist of one file from Entities folder and files from BaseClasses based on what are base classes of this entity.

### Example
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

The files that describes this entity keyvalues are: 
* Entities/func_plat
* BaseClasses/Targetname
* BaseClasses/Global
* BaseClasses/RenderFields
* BaseClasses/PlatSounds
* BaseClasses/BasePlat
* BaseClasses/ZHLT

Final website generated with these can be seen here: https://www.svenmanor.com/entity-guide/func_plat
