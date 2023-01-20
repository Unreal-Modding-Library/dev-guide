# C++
C++ modding is natively allowing C++ code to be run by the game. While this is by far the most powerful viable way to mod games, it is also dangerous as allowing uncontained C++ could allow malicious code to run. It is not nearly as easy for blueprints to be malicious as they do not have file I/O or web sockets support, unless explicitly provided by the developers or a plugin. You could introduce a special protocol for C++ mods to be uploaded e.g., by running all mods through Virus Total, or requiring that the source code is kept open source, etc. But it’s entirely up to you how you want to handle the risk if you choose to go down this otherwise excellent route.

To best provide C++ support, there are two methods:
- Providing an API
- Building modularly

Later, in the case studies section, I will go over examples from cyubeVR that provided an API and Satisfactory that built modularly.

## Providing an API
If your game heavily leans on C++ code and exposes very little to blueprint, providing an API could be a good option. The usual method to go about doing this would be to produce a template C++ project with all the functions that the game calls/exposes inside of it. Modders can then add their code inside of the functions, build the DLL and the game will call to the DLL during runtime. For example, the project could have a `Tick()` function that runs the code inside of it every tick. 

The downside to providing an API, aside from the security issue I mentioned earlier, is that if you want to provide any UE-specific types, you will have to reconstruct them inside of the template C++ project manually. But that may be legally questionable, by the statement of the [Unreal Engine EULA](https://www.unrealengine.com/en-US/eula/unreal) section `4.a.i`. 

This could be extended to providing a general scripting system API, such as Lua, but still has the same downsides.

## Building modularly
There is a native feature in Unreal Engine that few people know about, called Gameplay Modules. It is where classes sectioned by module are compiled into DLLs, rather than one monolithic binary. I won’t bother condensing what is already explained in the [UE documentation](https://docs.unrealengine.com/4.27/en-US/ProgrammingAndScripting/GameplayArchitecture/Gameplay/) for it, since it is already quite short. 

If a game is set to build modularly instead of monolithically, it can then load any other DLL inside of the `Plugins/` folder, even in shipping builds. A modder can then create a C++ plugin inside of UE, where the entire core UE API is exposed, and they can load it as a "plugin mod" into the game. The plugin can do anything the game’s normal C++ can do – reference, change or create assets. For this reason, this method is by far the most flexible and opportunity-inducing out of any in all of UE mod support.

There is only one game that I know of that has ever used this method for community mod support – Satisfactory. Therefore, I was able to ask the developers of this game – Coffee Stain Studios (CSS) about any drawbacks that they observed:
- Increased code size. In fact, executable size is decreased to nothing, but you get quite a lot of relatively small DLL files instead.
- Slightly increased start-up time and memory footprint. Don’t expect any numbers there, but "it’s really insignificant", according to CSS.

If you have not made any significant commits to the engine for your game, the bare minimum you can do to change to modular is changing `LinkType = LinkType.Modular` in the game target. 

Then future actions depend on the severity of the changes. Changes that are binary compatible with the stock engine do not need to be shared. If there are changes affecting binary compatibility – e.g., adding new properties, changing or adding virtual functions – they need to be shared with modders. The only legal way to share your engine patches is to fork the UE repository on GitHub and commit your changes to the fork. But if your changes are binary compatible, you can potentially skip that. 

If you would like to know more about this method, I highly recommend reaching out to the Satisfactory developers and asking them directly. 