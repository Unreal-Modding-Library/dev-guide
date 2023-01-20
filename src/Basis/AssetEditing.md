# Asset editing
As you know, Unreal Engine is open source, meaning that anyone can look at the code to see how certain systems work to try and reverse them. This is precisely what happened with the various cooked asset formats (`.uexp`, `.uasset`, `.ucas`, `.utoc`, `.umap` etc.) and [several tools](https://github.com/Unreal-Modding-Library/Tools#asset-editors-parsers--explorers) have been developed to make exploring, parsing, and editing these files as easy as possible. 

The most basic form of asset editing is just changing the default values of primitive variable types like strings, floats and booleans. It can be done on every engine version by all asset editing tools. A typical use case would be changing the damage of a weapon. 

The next level up from that is changing references to classes and objects, for example switching a component on an actor from one asset to another. Asset editing can go much further with super advanced techniques, but you get the point. 

There is also localization editing, where the localisation files, that have the extension `.locres`, are edited, since that is usually where many of the games’ strings are kept. This is handled by a [separate tool](https://github.com/Unreal-Modding-Library/Tools#locres-editors).

Asset editing is the most accessible method as many tools and documentation exist for it, but it is also quite limited without getting really technical.
