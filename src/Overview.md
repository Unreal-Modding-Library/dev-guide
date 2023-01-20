# Overview
Epic Games have stated in [this forum post](https://forums.unrealengine.com/t/got-general-modding-questions/34572), that "Unreal Engine 4 has been designed with modding in mind". They then go on to explain that since the engine source is available, and there is great documentation, mods have a lot of potential. While this is certainly true, which you will discover throughout this post, it is evident that even Epic Games have no idea of the true potential of mod support within Unreal Engine games.

## Misconceptions
"All mods are cheats!" It depends on the type of game, but generally this is a closed-minded way of thinking. You do not have to look far to see thriving modding communities that have completely changed the game in a positive way. Minecraft is the most well-known example. While they are both "modifications," mods and hacked clients should not be considered the same. I am vehemently against cheating in any game – because like most gamers, I have suffered from games with terrible cheating problems. If mods or methods have any overlap with the potential to be used for malicious purposes, I will discuss it.

I have seen a couple of indie game studios dismiss mods because they think that modders are trying to undermine them by adding features that fit the game’s style to make them look incompetent for not adding such features themselves. While this does have some reason – players may ask for a feature and the developers see that it does not fit the direction of the game they want to go in, thus making players angry – nobody thinks like that. You have got to think, why would someone spend tens or hundreds of hours of their life to create interesting content for a game? Because they are passionate about the game and want to see if they can improve the experience for others. 

The most important thing that mods offer a game, is "a second life." If official mod support is enabled for a game, and is easily accessible, it will take a significantly longer time to lose players after development stops, as well as it being more interesting alongside normal updates. The game gets content for free, and in many cases more sales because of certain big mods. I know plenty of people who have bought games because of mods, like flatscreen to VR (Virtual Reality) mods.

*feedback loop diagram maybe?*

One extremely common and ignorant misconception that I see a lot is something like "mods are bad because they allow you to rip our art/audio assets out of our game." Which is just not true – there are plenty of tools – that are not mods – that make it surprisingly easy for anyone to do, so really there is no hope if you want to stop your assets from being ripped. Asset encryption exists, but of course there is another tool and several methods that exist to crack the key anyway. If modding did not exist, the asset ripping problem would not change. By using an engine with source code available to anyone who can make an Epic Games account, you are accepting this risk.

While I agree that ripping assets from games is a big problem, it is extremely useful when making some mods. For example, if a mod wants to make an edit to a model, they can rip the mesh and its skeleton and use them as a template to edit the model rather than having to remake from scratch. But modders should be aware of the terms of use/legal policies for each game, so developers should make them as clear as possible.

The final thing I want to mention is that there are a few studios that have dismissed modding as an annoyance due to the assumption that players using mods can clog up the crash report stack with mod bugs. This is certainly a problem, which is why it is vital that a system is implemented for differentiating between modded games and vanilla games, in order to filter through crash reports. UE makes the crash reporting system highly configurable, so combined with detecting mods via the mod support system, it is not difficult. In some circumstances, mod crashes have brought light to previously unnoticed, subtle issues with the core game systems, so they can be useful.

## Genre of game informs types of modding
There are several factors that informs the type of modding that should be done on a game. 

The most obvious thing is what type of game it is. On the one side, if it is a competitive PvP game, should it support modding at all if it could be easy for a player to gain an advantage over others? And on the other, if it is a singleplayer sandbox game, what reasons are there to not add mod support? 

A particularly crucial factor is the engine version that the game runs on. Typically, the "best" engine versions for modding are 4.25/26/27, as they have had plenty of time to mature, thus have the most tools developed for them. Typically, any game 4.19+ is moddable to a high enough standard to make it worthwhile, and any game lower than this will require a significant amount more work from community tool developers. 

If the game makes heavy edits to the engine source, like many games do, it can make it significantly more difficult to mod. 

*Talk about switch between UE4 and UE5 maybe?*