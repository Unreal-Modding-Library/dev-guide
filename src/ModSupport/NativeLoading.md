# Natively loading mods
To natively load mods, there are a few options:
- Using a [marketplace Pak loader plugin](https://www.unrealengine.com/marketplace/en-US/product/pak-loader-plugin) (optimal)
- Using the [SimpleUGC](https://forums.unrealengine.com/t/inside-unreal-adding-mod-support-with-the-simple-ugc-plugin/147657/57) plugin
- Writing your own system

You will also need to produce a standard for blueprint names, install folder hierarchy and naming, that you must communicate to modders to conform to, but I will discuss this later.

This does not just apply to blueprint mods. You can still use it to mount and load in assets for the other modding types like audio, asset editing and visual. Since you are mounting every asset inside of the pak file regardless, any asset replacing an existing one will still work in the same way as the normal Pak patching method.