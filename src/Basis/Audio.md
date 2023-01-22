# Audio
The quality of audio modding is heavily influenced by the sound system that your game uses. The best system is the default UE sound system that was introduced in UDK (UE3). There are also the FMod and Wwise middleware that many games use, but frankly, they are rubbish. They are limited and a pain to mod since they are closed source and use [propriety formats](https://github.com/Buckminsterfullerene02/UE-Modding-Tools#audio). I get them being used by non-UE games or games developed before the UE sound system existed, but any new games using them baffles me. 

The extent of modding games using WWise or FMod is just by directly replacing the audio files. There is nothing more modders can do, without using blueprints.

Audio modding for games using the UE sound system has a slightly higher bar than asset editing, in that modders need to install the version of Unreal Engine that their game uses. The general pipeline for all audio mods, is recreate the audio asset with the same path and name inside of an Unreal Engine project with the desired changes, then cook and package from UE into the pak file.

There are 3 methods of audio modding for games using the UE sound system:
- Directly replacing sound waves. Modders can import their .wav/.ogg audio file into the same name and location as the original they wish to replace

- Replacing sound cues. If a modder recreates a sound cue in the same name and location as the original, they can:
    - Make their own sound cue graph

    - Use as many custom sound waves as they want

    - Use custom attenuation, concurrency or submix settings

    - Recreate other referenced assets in the original, such as sound class, and reference them in their new cue. This is a vital component that modders should follow if they want their mods to be able to be controlled by the game’s audio sliders, ducking and other systems controlled by those assets
    
- Replacing other audio asset types, like making custom sound class or submix hierarchies, replacing attenuations, sound curves, etc.

If you want to get an idea of any of these methods, you can have a skim through the [audio modding guide](https://mod.io/g/drg/r/drg-mods-a-comprehensive-guide-to-audio-modding) for the game Deep Rock Galactic. The examples use that game, but every technique is transferrable to any other using the UE sound system.

As you can see, all audio modding is, is just replacing existing files. If modders want to use audio in more advanced contexts, like adding entirely new sounds to places that do not already have them, then they must use blueprint modding, explained later. 
