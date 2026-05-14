# Numidium

>[!NOTE]
>DEPRECATED in favor of the [Rust Version](https://github.com/krateng/numidium)

It seems silly to go through the trouble of running Windows Mod Managers via Proton only for them to then go through extra trouble to make things on Windows work that already are much easier on Linux.

Numidium uses OverlayFS, which can simply put any number of layers on top of the base game directory and then mount the result on the very same path, making the process completely invisible to Steam or the game itself, which also makes dynamic mods like LOD generators much simpler.

Numidium is not a mod manager in the same sense that e.g. Vortex is. Instead of an interactive window with the ability to edit your load order, mod configuration etc. on the fly, Numidium is centered around the concept of having your modlist stored as repeatable instructions that can then be deployed at any time. For this, Numidium uses so-called Brassfiles. Their syntax should be familiar to anyone who has used Docker:

```
GAME skyrim64
INCLUDE base_fixes
INCLUDE graphics_enhancers
MOD immersive_sweetrolls,options=16KTextures&ExtraIcing
MOD blackpink_main_menu_music_replacer
```

Right now, I'm just experimenting a bit, but you can already try it out with:

`python -m numidium deploy mymodlist`

where `mymodlist.brass` contains your load order, and all the mods are in your configured mod folder.
