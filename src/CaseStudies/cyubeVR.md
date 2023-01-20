# cyubeVR
[cyubeVR](https://store.steampowered.com/app/619500/cyubeVR/) was the first game where I took what I learnt from DRG and applied it to a game that wanted mod support. The developer had 7 years of experience with Unreal Engine and many years of being active in the Unreal forums/slack group when I first spoke to him but had literally no clue about modding. This is partially what lead me to writing this document in the first place.

Since cyubeVR is a voxel game, all the voxel code is bespoke and written in C++ for maximum performance. Therefore, normal blueprint mods cannot manipulate this system. But many of the game’s systems (e.g., weather) still use normal UE assets and reflected C++ so blueprint mods can manipulate those.

What the developer decided, was to produce support for 3 types of mods:
- Normal UE pak mods (including natively loading mods)
- C++ API for the Voxel system
- Custom blocks

For native mod loading, he used the marketplace pak loader. It took him less than a day to implement the system, once we had figured out the mod naming/folder hierarchy scheme. To this day, the system works perfectly.

When working on a mod kit tool, I came across nativized blueprints which caused me a lot of headaches. Since these assets were nativized for important performance gains, the developer just gave me access to a temporary build of the game on Steam with nativization disabled.

In order to support C++, the developer produced a [template C++ project](https://github.com/sbsce/cyubeVR-VoxelAPI-Modding) with all the exposed functions, Enums and properties that can be accessed. Modders can write code inside of certain functions that are then called by the game at runtime. For example, there is a function that is called when a block is hit by a tool, with input parameters such as the type of tool that hits the block, the position of the block and the type of the block. When the mod needs testing, the modder can build the project into the dll and store it in a certain location in the game’s Mods/ folder and the game will call to it.

The C++ API template does not need to recreate any UE types because the game does all the type conversions on its side, due to it only needing to use basic types such as string and vector. It does however recreate several Enums such as tool type. 

While there have not been any incidents yet, there is no solution currently in place to check C++ mods for malicious code. 

Custom blocks are just providing a format for new blocks with their own textures and recipes. Custom blocks have no functionality other than looks. When a user subscribes to a custom block mod, the block will show up in their block list in-game.
All mod types can be uploaded to the Steam Workshop via in the in-game mod menu.