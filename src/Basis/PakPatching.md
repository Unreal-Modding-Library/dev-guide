# Pak patching
This is the most fundamental part of UE modding because most forms of modding use it. “Pak” refers to the UE .pak file archive format that it uses to store all the cooked assets for the game. It is where mod assets get loaded into the game from.

Many games will have one monolithic pak file with everything inside of it, but others have “chunks” of files categorised by certain asset types, DLCs, levels etc; whatever the developers decide. This is important to know, because it means that the engine can mount multiple pak files from the Paks/ folder. 

So, knowing this, what happens when two or more pak files have assets in the same name and relative path? The pak that is mounted most recently replaces any existing assets. Mount order is decided alphabetically. For example, if we have pak-chunk-0.pak and pak-chunk-1.pak that both contain the asset /Game/BPCharacter.uasset, then the asset in pak-chunk-1.pak will be the asset that is loaded because it “patches” over the top of the asset in pak-chunk-0.pak. 

If this is not already enough, UE has a [built-in system](https://docs.unrealengine.com/4.26/en-US/SharingAndReleasing/Patching/GeneralPatching/HowToCreatePatch/) for giving direct mount priority to any pak files that have the suffix “_p” in their name. 

Modders can combine the above two methods, to always make sure that their mods are loaded into the game. Consequently, the basis of modding is replacing existing assets in a game with edited or entirely new ones.

Finally, it is important to know that custom C++ classes cannot be loaded into the game using pak files, since they are only for assets. But that is not such a big deal as you might initially think, which will be explained in the “Blueprint” section.
