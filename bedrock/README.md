## Advnaded: Installing custom settings on existing active server

1. Create a new world with the proper settings
2. When you create the world, you have to make sure the name of the world is the same.  By default it is `Bedrock level`
3. Search for the `level.dat` file on your new world with the new settings
4. Copy the new `level.dat` file into the the same level in your existing server
5. To double check, cat the `levelname.txt` file in both your systems and make sure they match





## Advanced: Installing addons onto an already existing world:
NOTE: We highly recommend giving the above sections a try first. The two methods above will work regardless of what format your addons are in, as long as you're able to import them into your Minecraft client.

Before getting started: if your addons are in .mcpack or .mcaddon format, before you'll be able to follow these steps, you'll need to extract the folders from inside these files. To do this, follow these steps:

Right click the addon .mcpack or .mcaddon file on your computer, hover over "Open With", then open the file with an unzip program of your choice like 7-zip or Bandizip.

Extract the folder addon folder to somewhere on your computer. 

To verify that every extracted properly, open the folder that was extracted and you should see a manifest.json file along with other files and folders.

## Setting up for installing addons:
1. Stop your server.
1. Login to your server with an FTP client like WinSCP, you can find our guide on how to use WinSCP here. 
1. Upload any behavior packs to the behavior_packs folder on your server, and upload any resource_packs to the resource_packs folder on your server.
1. Open the worlds folder, then open the folder with the same name as your active world.

Right click anywhere in the empty area on the right of the WinSCP window that contains a list of your server's files and folders, hover over "New", click "File", then type in "world_behavior_packs.json" if you're creating adding behavior packs. Repeat this process if you're adding resource packs, but name the file "world_resource_packs.json". NOTE: If you already have these files, you can skip this step.

Right click the .json files files that you created and click "Edit" to open the files in your system's text editor. We recommend using Notepad++. Be sure to keep these files open for the remaining steps.

### Locating addon UUIDs and versions.
Navigate to the behavior_packs or resource_packs folder on your server, open the behavior pack or resource pack you'd like to load, then right click the manifest.json file and click "Edit" and keep these files open.

Copy the lines in the header that contain the uuid and the version. They'll likely look like this:
```
"uuid": "e65d24fc-3154-42be-915f-45b9005eea40",
        "version": [3, 5, 0]
```
or this:
```
"uuid": "10017b89-cbdf-41f9-ba28-123abca8e07d",
	"version": [
		1,
		0,
		0
	]
```

### Adding your first addon to the .json files
1. Taking the uuid and version that were copied in the above section, paste them into the respective .json file. If you copied the uuid and version of a behavior pack, paste it into the world_behavior_packs.json file. The same goes for resource packs. If this is your first time adding a pack to the .json file, it should look something like this:

```
"uuid": "e65d24fc-3154-42be-915f-45b9005eea40",
        "version": [3, 5, 0]
```

or this:
```
"uuid": "10017b89-cbdf-41f9-ba28-123abca8e07d",
	"version": [
		1,
		0,
		0
	]
```
NOTE: If your version section takes up multiple lines, you can consolidate it by getting rid of the extra spaces and lines like this, however, you're welcome to leave it as is.:
```
"uuid": "10017b89-cbdf-41f9-ba28-123abca8e07d",
	     "version": [ 1,0,0 ]
```
2. Change the "uuid" text to "pack_id", then remove the comma at the end of the version line so that it looks like this:
```
"pack_id": "e65d24fc-3154-42be-915f-45b9005eea40",
             "version": [3, 5, 0]
```
3. Add square brackets ("[" and "]") at the start of and end of the file along with curly brackets ("{" and "}") surrounding the addon information like this:
```
[
        {
             "pack_id": "e65d24fc-3154-42be-915f-45b9005eea40",
             "version": [3, 5, 0]
        }
]
```
4. Save the changes, then startup your server to load the addon!

### Adding additional addons to the .json files
1. Inside the world_behavior_packs.json or world_resource_packs.json, add a comma after the last curly bracket, then create two more curly brackets just like you did with the first section. It should look something like this:
```
[
        {
             "pack_id": "e65d24fc-3154-42be-915f-45b9005eea40",
             "version": [3, 5, 0]
        },
        {

        }
]
```
2. Copy and paste the uuid and version from a manifest.json file into the blank space between the two new curly brackets, then rename "uuid" to "pack_id" and remove the comma at the end of the version section so that it looks like this:
```
[
        {
             "pack_id": "e65d24fc-3154-42be-915f-45b9005eea40",
             "version": [3, 5, 0]
        },
        {
	     "uuid": "10017b89-cbdf-41f9-ba28-123abca8e07d",
	     "version": [ 1,0,0 ]
        }
]
```
3. Repeat this process until you add all of the behavior or resource packs that you'd like to load on your server, then save the changes and restart your server to load the addons.

## Running into problems with the addons loading?
Try copying the .json file that was edited and paste it into a .json parser like this one. If there are any json formatting issues, it'll tell you where the problem is so that it can be fixed. You can also reach out to us at any time with the blue button in the bottom right corner of the page and we'll be happy to help!


---

# Creating custom blocks
1. Download: https://blockbench.net/downloads/
1. Download: 
   * https://github.com/bridge-core/bridge.
   * https://bridge-core.github.io/
1. Follow the tutorials:
   * https://youtu.be/494U6pSvbOg
   * https://youtu.be/MTkULBJJVwQ


### Blockbench
1. Download for your platform
2. Create a new project and call it whatever you want, but note that the name will be used in multiple place, so if you call it `test` make sure to use that same name in all the other inputs.
3. For simplicity sake the filename and the model identifier should be the same
4. For making a block, just keep the default texture size of 16 and 16
5. You can click on Layered Textures if you want to do make fancy colors or fancy texture maps.



---

# Builds
1. Wizard Tower: https://www.grabcraft.com/minecraft/unique-wizard-tower/other-193

---

# Resources
* Use existing models: https://www.youtube.com/watch?v=t6ciyxrU5Sk
* Create custom entities: https://www.youtube.com/watch?v=xoybMf05Jl8
* Companion Cube: https://youtu.be/z4-jTBo_n4o
* Custom food and weapons: https://www.youtube.com/watch?v=MTkULBJJVwQ
* Custom block: https://www.youtube.com/watch?v=494U6pSvbOg
* Making a sword from blockbench: https://www.youtube.com/watch?v=PTItYqKSBwo
* Arts By Kev:
    * https://www.youtube.com/watch?v=K0O3H0q0S74
    * https://www.youtube.com/watch?v=GQtXlmy2xTE
    * https://www.youtube.com/watch?v=N3CGOGYJ0e0
    * 
