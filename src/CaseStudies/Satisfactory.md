# Satisfactory
[Satisfactory](https://www.satisfactorygame.com/) is a primarily singleplayer automation game. This lends itself to modding. Luckily, the developers recognised this and released the game with PDBs, despite it doubling the download size. The PDBs provided allowed for a community mod launcher to be made very early on. 

In 2021, Satisfactory became the first UE game that I know of, that switched to the modular build type. It was by the modders’ request, and it took them roughly a year to make the switch after internal testing alongside normal development. As discussed previously, it allowed for C++ mods to be loaded as plugins which instantly boosted the possibilities of almost endless to literally endless, while also making the viability of complex mods possible due to the increased efficiency.

Therefore, the community could heavily expand their mod support capabilities. They created their own 3rd party mod browsing website, which was interfaced by a mod launcher that could manage mods, find new ones, etc. It then installs selected mods ready for the game to be loaded.

Additionally, since the mods are plugins, they can interface directly with the UE core C++ API, meaning that they could easily dump all the information about the C++ headers and assets in the game and produce their own [mod kit](https://github.com/mircearoata/satisfactory-modding) for modders.

A downside to this, as discussed, is security. Giving people the ability to upload uncontained C++ that is executed can be very dangerous, which is why all mods uploaded to the site are ran through [VirusTotal](https://www.virustotal.com/gui/home/upload). As far as I am aware, in the last few years, there have not been any incidents.

Although the developers intended on official mod support from the first launch of Early Access, it is clear that the community’s system is so strong that they don’t need to do anything themselves, aside from providing help with internal information, and the changing of the build type to modular obviously.
