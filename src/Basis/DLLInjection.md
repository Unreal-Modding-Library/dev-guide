# DLL Injection
This method is used by modding tools rather than mods themselves, with a couple of exceptions. Injection is either done by using a DLL injector or by proxy injection using the DirectX DLL xinput_3.dll. Since UE games usually have the same function names, the program will attempt to locate these in the memory and hook into them to achieve a certain purpose. 

However, since games use different engine versions and have their own custom engine implementations, the "array of bytes" that the tool will try to find for a specific function can change. So, it may be up to the user of the tool to locate the AOBs for the game they are trying to inject into.

*Maybe something about anti cheat systems?*

Yes, there are "mods" or tools that use this method that are specifically designed to enable cheating in games, and I condone those. However, it is still extremely important for modding tools because these programs can provide so much useful information about the game.

The types of tools that use DLL injection usually fall into a few categories:
- Console unlockers – re-enables the in-game console if it has not been stripped from the game completely and allow unstripped commands to be entered like normal
- Free camera – allows the player camera to be detached and "flown" around the level
- Dumping object memory – produces files of internal object information such as reflected C++ headers and blueprint bytecode. This is by far the most useful for tool developers
- Mod loading – mounts pak files and loads mod blueprint actors 
