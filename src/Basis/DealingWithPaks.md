# Dealing with Paks
To get access to the assets inside of a pak file, modders will need to unpack it. There are plenty of tools that can achieve this, although if a modder already has the correct engine version installed (which they can find out by right clicking the game’s binary and looking in the details tab) they can call to the UnrealPak utility by command line or batch script. 

Once modders have created their edited or new assets, they need to pack only the assets they intend to be replaced, back into the pak file, again by calling the UnrealPak utility.

The quality of the modding experience can differ depending on what packaging settings have been defined in the game’s project, but obviously the people responsible for these settings need to weigh up these settings with their own circumstances:

Name | Engine versions | Default | What ON does	| What OFF does | Optimal
-----|-----------------|---------|--------------|---------------|--------
Use IO Store | 4.25+ | OFF for 4.25-4.27, ON for 5.0+ | Produces `.ucas`/`.utoc` file types within the pak file, which are difficult to work with and requires considerable extra work to get them loaded into the game like normal formats | Produces `.uasset`/`.uexp` files within the pak file, which are the easiest to work with | OFF
Un-versioned Assets | 4.25+ | OFF, ON for 5.0+ | Removes version signatures from asset headers. Makes them difficult to mod, as asset parsers depend on reading the versioning information in the headers for deciding on how to parse them	| Keeps version signatures in asset headers | OFF
Event Driven Loading | At least 4.17+ Check | ON | Produces the `.uasset`/`.uexp` files and is highly suggested for the best modding experience	| Produces only the `.uasset` files | ON
| Blueprint Nativization | At least 4.17+ check | OFF | For any blueprints that are added to the whitelist, and every userdefinedstruct/enum, their code is "decompiled" to C++ rather than bytecode as an asset, which means that the blueprint cannot be "viewed" by modders with any tool | Cooks blueprints as `.uasset` files | OFF
Generate Chunks | At least 4.17+ check | OFF | Combined with allow ChunkID assignments asset action being on, it packs assets into specified pak chunks. This makes lives for modders more annoying than anything because having to unpack multiple chunks is a pain and can become messy | Packs everything into one pak file | OFF
Use Pak Encryption | At least 4.17+ check | OFF | Requires an encryption key to be generated and that key must be provided when unpacking the pak. Modders can use tools and a bit of brute force to obtain these keys, but it can be annoying if a game does not need it (I.e., not a game where mods can be used to gain an advantage over others) | Pak file will not be encrypted | OFF

The files that are stored in the .pak files are cooked. This means that they cannot be copied into a UE project and edited inside of the editor. There are a few exceptions, for example data tables and string tables – and to do that you need a [couple of configs](https://gist.github.com/Buckminsterfullerene02/6dc5256790457cc7d30693bf37d71e3f) – but it’s only really useful for basic data mining. 