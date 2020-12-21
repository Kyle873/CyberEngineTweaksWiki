You can write commands directly in the console but for more complex scripts, you may use files.

The console will look for files where `Cyberpunk2077.exe` is located, ideally you will put your files in a folder dedicated to that, for example official `Cyber Engine Tweaks` files are located in `plugins/cyber_engine_tweaks/scripts`, here we will assume you created a directory `scripts` and place your lua files there.

You can execute your file by typing `dofile "scripts/myfile.lua"` in the console.

## Getting started

There are 2 function types and 2 handle types.

### Global functions

They do not need a handle and are all located in the `Game` object.
Sample:
```lua
Game.PrintHealth()
-- or
Game.AddToInventory("Items.money", 500)
```

### Handle functions

They require a handle (more on that later). Assuming you have a `player` handle:
```lua
print(player.IsNaked())
print(player.IsMoving())
player.OnDied()
```

## Handles

Handles are a way to pass an object to the function. For example `IsNaked` makes no sense without telling the engine for which object we want to know this information.

### Singleton

These handles are static, there is only one in the game, for example the `gameTimeSystem` is a singleton so there is no need to tell the script engine which one you want. That being said you **need** a singleton handle so it knows you want to call a function on that system.

Sample:
```lua
gameTime = CreateSingletonHandle("gameTimeSystem")
print(gameTime.GetGameTime())
gameTime.SetGameTimeByHMS(12,0,0) -- 12h0m0s
```

### Regular handles

These handles are not unique, for example the game contains multiple NPCs so there are as many handles as NPCs. Currently as far as I know we can only get the handle of the `player` by calling the global function `Game.GetPlayer()`.

Sample:
```lua
player = CreateHandle("PlayerPuppet", Game.GetPlayer())
if player.IsNaked() then
    player.OnDied() -- kill the player if it's naked
end
```
