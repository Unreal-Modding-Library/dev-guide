# Mod kits/SDKs
If you want a thriving mods community, you should provide tools to make things either possible at all, or just easier. While community created tools can cover many bases that developers won’t, it always makes sense for official tools to be created. 

While I create mod kits for multiple games, I can see the scenario where I get burnt out and stop maintaining my tools. Even though I try to document as much as possible, if no one picks up the slack, entire modding pipelines can grind to a halt or be reset to square one. If the developers created official mod kits, there is an obligation to keep things maintained and documented clearly so that the next developer can continue the work.

But what sort of stuff could modders expect in a mod kit?
- The game’s C++ headers (.h files). Modders can get all reflected headers themselves, but it is always worth more to have the ones from the developers with any comments explaining what they do/are for

- A "middleware" interface consisting of reflected C++ headers that allow blueprints to interface with an internal C++ system (such as a bespoke tech tree system) or a paid marketplace plugin (such as the voxel pro plugin). This is highly sought after as developers can:
    - Avoid using C++ modding which may pose a security risk

    - Control exactly which parts of a system mods can access, and how
    
    - Provide the ability to mod previously "unmoddable" systems e.g. a plugin without reflected headers, so couldn’t be accessed via blueprints

- Code for the game’s engine fork if it has one. The best way to do this would be to have someone make a fork of the UE source code on GitHub and then upload their edits to that as a mirror of their own project’s one. Due to the UE EULA, the engine source MUST be distributed via an Epic Games verified path, such as a fork of the engine or via the marketplace

- Custom in-house plugins and/or editor utilities that offer functionality that can’t be found anywhere else. Obviously, paid marketplace plugin source cannot be shared without permission from the author

- Certain assets (ideally all of them) like blueprints that modders could modify directly in-editor. Modders can technically already obtain these from parsing cooked uasset files, but it is a lot of work and can be error prone

- Following on from the previous, animation assets such as animation sequence and skeletal mesh. In FBX format, if possible, but as uasset can suffice too. This saves a bunch of time ripping the assets from the game using various tools, which can also be wrong when a game uses a different forward axis for skeleton bones or other things 

In our dreams, we can get the game’s UE project as a download with all the C++ and assets, but obviously, that is not something anyone expects... except that it is partially possible due to some community made tools, that I will describe in the next section.

## Creating good "conditions" for modding your game
Aside from mod kits, there are a few ways you can improve the quality of mod support:

- C++ enums cannot be edited, so use user defined enums where possible, or not at all

- Make as few major engine edits as possible – if you do, and you need to distribute your fork to modders, it doesn’t stop being a huge pain

- Don’t hardcode values in your C++. This is a bit of a no brainer, but you’d be surprised how much I’ve seen games do this

- Use data assets where possible – they are very easy to edit/add to/create frameworks from, and they make general project quality clean

- Add plugins to game project on request, e.g., `SteamVR/OpenXR` if modders want to make a flatscreen to VR mod

- Provide nice blueprint functions in a C++ `BlueprintFunctionLibrary` such as reading/writing strings from/to files (and making it clear what path roots are)

```cpp
UFUNCTION(BlueprintCallable)
bool WriteToPlainText(const FString& Filename, const FString& TextContent, FText& OutError, bool Append);

UFUNCTION(BlueprintCallable, BlueprintPure)
bool ReadFromPlainText(const FString& Filename, FString& OutTextContent);
```