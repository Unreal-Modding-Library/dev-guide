# Visual (textures, models, animations)
This is by far the most popular kind of modding. If a game’s files can be unpacked and mods loaded with normal Pak patching methods, it is almost guaranteed that visual modding can be done on it. They can be low effort or very complex, high effort mods or anything in between. They are also client-side only, which means that they can usually be loaded without the server knowing and thus won’t affect the other players (unless created with malicious intent, e.g., making world models transparent).

The process for most visual modding for the longest of times is opening [UE Viewer](https://www.gildor.org/en/projects/umodel) (also known as UModel) and exporting the texture/model/skeleton/animation from the cooked assets, into a format that can be imported into Blender, 3DSMax or whatever other software that is being used. 

If the modder wishes to import the asset into UE, they will need to use another tool to export from their software of choice into FBX. In order to replace the asset, they must import into UE with the same name and location as the original and then they can cook and package their mod. 

In 2022, there were tools such as [this Blender Plugin](https://github.com/matyalatte/Blender-Uasset-Addon) popping up that allows models/animations/skeleton .uasset files to be imported directly into Blender. Modders can then make their edits and export the asset straight back to the .uasset format and replace the original in the game. This is ground-breaking because it no longer requires anyone to install Unreal Engine to make model edits.

If you wish to know more about visual modding, there are plenty of videos and guides out there that explain the various methods and processes in greater detail.