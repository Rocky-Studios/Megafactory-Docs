# Megafactory Modding Documentation

## About
Welcome! Though writing a mod may seem as complicated as writing a whole game, because it is usually hard to adapt your code to work with someone else's, this guide should simplify the process so anyone can make a mod.

Megafactory is made with the <a href="https://godotengine.org/" target="_blank">Godot Engine</a>, and so to make more complicated mods you will also need a basic understand of it.

Megafactory is built from the ground-up to be easily moddable, and so all of it is documented, and most functions available inside the engine are available here. 

!!! danger

    It is not recommended you modify core engine functions. This can cause unstability and your mod might not be accepted on the offical modding website.

Mods are written in C#, and some prior coding experience is recommended, either in C# or a similar language like Java or Javascript. If you do not know how to code in C#, it is recommended you take a few days to learn the language. While I will do my best to describe how to write code, this is by no means a coding tutorial and do not expect to learn to code from making a mod.

**This guide is made for Windows 10+ with <a href="https://visualstudio.microsoft.com/vs/community/" target="_blank">Visual Studio Community Edition</a> and <a href="https://blender.org" target="_blank">Blender</a>.**

## Publishing your mod
??? guide info
    If you're done with the first public release of your mod, you can upload it to [megafactory.rockystudios.net/mods](https://megafactory.rockystudios.net/mods) so other people can download it from within the game.

    Your mod might be rejected, and we will provide a good reason why. It will usually be rejected if it poses a security risk to users, and we will provide a fix.

    <strong style="color: red;">DO NOT UPLOAD YOUR MOD ANYWHERE ELSE</strong>
## Best Practices
So, you're ready to make a mod. But before you start, it is recommended you have a readof this section, so that you can do things right from the start and not have to rewriteor redesign your mod later on.

### The file structure
Obviously, you can't just put down files in the mod folder and expect things to show up in-game. First, you need to locate your mod folder. On Windows (which is intended for this guide), the folder is `"%LocalAppData%\Rocky Studios\Megafactory\mods"`. You can simply run `⊞+R` and paste this path. If this folder does not exist, just open the game once and it should generate it.

Inside the mods folder, there is first the package name of your mod, such as

- If your mod is developed by you or just a casual group of friends, `me.{yourname}.{yourmod} eg. me.johnsmith.mycoolmod`

- If your mod is an organisation, `com/net/org.{yourorganisation}.{yourmod} eg. org.johnsmithco.ourcoolmod`

!!! info

    If you have a website, eg. `johnsmithco.org`, you should flip it around to `org.johnsmithco` and then add the project name.

This must all be lowercase and follow this format


Inside this folder you have different versions of the mod. You could have a folder for `0.0.0.1` or `1.2.3.4`. This makes it easy to have multiple versions of the same mod installed (or modpack, which I'll get to in a bit). Inside this version folder is where all your mod files go.

### Versioning

So, mods and modpacks have a `x.x.x.x` versioning format. But what does that mean? Well quite simply, it is 4 numbers that identify different stages of your project.

**rewrites** are HUGE versions of your project. It starts at 0, then when you release your project it gets incremented to one. For it to get to 2, you must rewrite the majority of your code.

**release**, is what MAJOR version your project is at. When you initially make your project, it will be 0. For each MAJOR rewrite that you do, consisting of fixing all the bugs you can and optimizing considerable, you may increase your release number.

**update**, is what regular update of that version your project is at. Each update should consist of a couple bug fixes (if there are any) and at least 1 moderate-big feature.

**hotfixes** are little updates to your project. They should include at least 2 bug fixes but no major features.

!!! warning

    If you have any less than 4 numbers or do not include the dots between them, your project will not be added to the game and in some cases it may crash.

## Modpacks

Modpacks are simply collections of mods optimized for performance and compatibility. They are stored in the `Megafactory/Modpacks` folder instead of the `/Mods` folder. Currently, they consist of only a simple JSON file with its name, version and the mods, their versions and config if they have one. When you install your first mod, a modpack is automatically created.

!!! info

    JSON is a data format with the extension `.json`

    C# has the `.cs` extension

# Creating your first mod
[**Now you can move onto starting your first mod!**](/first-mod/)

