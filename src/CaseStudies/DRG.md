# Deep Rock Galactic
Dwarves?! In space?! Shooting bugs?! Getting drunk?! That’s [DRG](https://www.deeprockgalactic.com/), a co-op PvE shooter with a great modding scene. I am slightly biased as I create and maintain the mod kits for the blueprint and audio mods. I don’t make all the tools, since there are some game generic tools that we use, but the [main ones](https://github.com/DRG-Modding/FSD-Template) are made by myself. I also wrote and maintain the guides for [audio](https://mod.io/g/drg/r/drg-mods-a-comprehensive-guide-to-audio-modding) and [blueprint](https://mod.io/g/drg/r/how-to-blueprint-mod) modding.

When I first started modding this game mid-2021, there was no official mod support. Someone created a blueprint mod loader for the game by replacing the credits widget asset, since it is always loaded and doesn’t have any game-changing functionality (sorry devs). The mod loader also acted as a shared settings window, where blueprint mods with widgets are placed into a common window with tabs for each mod and other information provided. This solution was pretty good for the time, but mods were distributed via README links on a GitHub repository and the mod loader had hardcoded mod slots. 

Around November 2021, official mod support came in the form of native mod spawning, a mod management window in the game with an interface to a 3rd party website ([mod.io](https://mod.io/)) where users can browse/subscribe to mods, look at guides, etc.

The native mod spawning method that they chose to use was the SimpleUGC plugin, but very heavily modified. In fact, they modified it so heavily that it pretty much became its own independent system that mounted pak mods in the same way as the marketplace pak loader plugin. 

The only difference is that they also added hot reload support – meaning that the mods can be unloaded and reloaded without the game having to be closed. This is a big deal for the game because there is a lot of time switching between a private lobby and a multiplayer lobby and having to restart the game every time some mods are enabled/disabled/updated would be a massive put-off for users. I did request for the developer of this system to create an explanation of how it works, since it is a custom engine change, but their contract states that they are not allowed to, so sadly I cannot share this with you.

There are also many complications with modding categories, since many players expressed concerns that players could use mods to gain levels much faster than they did, thus inflating the “veteran” status of having a high level. So, the developers introduced a system where each mod uploaded to mod.io is assigned one of three categories. Each category limits what can be done in the game, such as using a different player save and turning off achievement progress. This has all added a lot of extra complexity with their own issues.

Since so much of the system is custom made, there were, and still are, a lot of subtle issues with mods. For example, that inconsistent mod loading order issue I described earlier. Additionally, the integration with the mod.io plugin that pulls mods from the mod.io API is quite broken still because there are bugs where the game redownloads all the mods when you load it up, for no apparent reason. 

The takeaway from this case is once again reinforcing the idea of “no step is the best step”. Unless your game is really complicated, don’t try to make overcomplicated systems like they did. And research all the possible mod loading methods before implementing one! 