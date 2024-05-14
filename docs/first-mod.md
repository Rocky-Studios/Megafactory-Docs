# Creating your first mod


There is a wizard to create all the necessarily files for a mod in-game.

1. Open the mod menu

2. Press `Create Mod` at the bottom right

3. Follow the steps and your mod will appear in the mods folder (`AppData/Local/Rocky Studios/Megafactory/mods`)

If for whatever reason you would like to do it manually, you can.
??? info "Manual Setup"

    Create a folder in `AppData/Local/Rocky Studios/Megafactory/mods/Mod.Name.Here/Mod.Version.Here`


    eg. `AppData/Local/Rocky Studios/Megafactory/mods/me.johnsmith.MyCoolMod/0.0.1`
    Create two files in the folder called **mod.cs** and **mod.json** (case is important)
    Fill out `mod.json` like this:
    ```json
    {
      "mod-name": "MyCoolMod"
    }
    ```
    And `mod.cs` like this:
    ```cs
    using Godot;
    using Megafactory.Scripts;

    namespace MyCoolMod
    {
        public class Main
        {
            //Called when the game is loaded
            public void Start()
            {

            }

            //Called every frame
            public void Update()
            {
              
            }
        }
    }
    ```

!!! info
    If at any time you would like to skip ahead or get more detailed info, you can check out the API Reference or the examples on the left.

## Getting your mod to show up in game
Now that you have your project files set up, we can start making something cool! But before we do anything like that, we need to check that our mod is being loaded correctly.

At the top of your file, next to the `using`'s, add a new statement:
```cs
using Megafactory.Scripts.Debug.Logger;
```
Inside your start method, add this line of code:
```cs
Logger.Log("Hello world!");
```
!!! info "Documentation"
    [Log](/API%20Reference/Debug/Logger/Log), [Logger](/API%20Reference/Debug/Logger)

Then open your game, make sure your mod is enabled and press Recompile. You should see some output at the bottom left that says "Hello world!". Try changing the text inside the double quotes, or try doing some math.
!!! info "Tip"
    You can combine strings (text) using the `'+'`, like
    ```cs
    Logger.Log("Five plus two is " + (5 + 2));
    ```
    Make sure to put any math inside parentheses, otherwise the text and math might be combined incorrectly.

??? bug "Not working?"
    Here's some things to try:

    - Try disabling all other mods

    - Read the error message carefully, it usually tells you exactly what is wrong
  
    Still not working? Ask someone online or in discord!
  
**If the message is correctly shown, great job! You have just coded your first mod! You can now go to the next step.**

## Adding a material
Different shapes (gears, rods, etc.) can be made from different materials, which all have different properties. This section will teach you how to modify the game registry to add a new material, tweak its properties and add a recipe.

!!! info "Documentation"
    [Material](/API%20Reference/Material)

First, you need to add a using statement for the material class:
```cs
using Megafactory.Scripts.Material;
```
Create a new material and assign the values in the constructor.
```cs
Material myMaterial = new Material("My Material");
```