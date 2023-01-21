# SimpleUGC plugin
The "Simple User Generator Content" [plugin](https://forums.unrealengine.com/t/inside-unreal-adding-mod-support-with-the-simple-ugc-plugin/147657/57) was originally developed by Epic Games for a mod kit for the VR FPS game Robo Recall by Epic Games. I know a couple of games that use it, except that they both had to heavily modify it just to fit their needs, which are mostly met by the marketplace Pak loader plugin I talked about previously. 

SimpleUGC’s way of handling mod files is ignorant of the fact that we can just dummy reflected C++ headers and use them, and you don’t even need to specify the category of "user generated content" in the macro. There’s no point in having it when everyone can use every reflected C++ header in the game regardless of the category or macro flags. 

Additionally, their system with the `MakeReplaceableActor` component is redundant because modders can replace anything by placing the same asset type in the same name and location as the original asset, as I have explained previously. So, since we can just do it for everything anyway, it will save a ton of work not having to add that component for everything that you "want" to be replaced.

The need to create a custom game instance makes modding unnecessarily difficult for modders. If something is not loaded by the normal game instance, then it may be on the UGC asset registry, so modders will need to know to do additional checks for that as well. It is a small thing, but yet another cause for potential headaches further down the line.

But the main reason I do not like this plugin is that it requires the developer to produce a "mod kit" just to allow modders to actually create their mods within UEE. This mod kit is not related to providing any game assets to aid with modding itself, but rather framework files. The best step is no step - it is not ideal as it increases the bar for modders and restricts what can be done. 

The plugin may work for you, but to be honest it’s a lot of extra work than needs to be for both sides and if you do end up modifying it, you’re way more prone to annoying crashes and bugs that makes good mod support harder to reach. 
Of course, I recommend that you still explore this option yourself; don’t just take my advice and run with it. 