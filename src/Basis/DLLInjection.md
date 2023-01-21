# DLL Injection
This method is used by modding tools rather than mods themselves, with a couple of exceptions. Injection is either done by using a DLL injector or by proxy injection using the DirectX DLL `xinput_3.dll`. 

In a nutshell, for a program to hook into a game, it needs to find the address of the function it wants to hook into. This is done by searching for an "array of bytes" (AOBs) that is unique to the function. 

However, since games use different engine versions and have their own custom engine implementations, the AOBs that the tool will try to find for a specific function can change. So, it may be up to the user of the tool to locate the AOBs for the game they are trying to inject into.

Some other things that can cause bytes to change include compiler and compiler version, compiler flags and build mode (debug, shipping, etc).

Yes, there are "mods" or tools that use this method that are specifically designed to enable cheating in games, and I condemn those. However, it is still extremely important for modding tools because these programs can provide so much useful information about the game.

The types of tools that use DLL injection usually fall into a few categories:
- Console unlockers – re-enables the in-game console if it has not been stripped from the game completely and allow unstripped commands to be entered like normal

- Free camera – allows the player camera to be detached and "flown" around the level

- Dumping object memory – produces files of internal object information such as reflected C++ headers and blueprint bytecode. This is by far the most useful for tool developers

- Mod loading – mounts pak files and loads mod blueprint actors 
