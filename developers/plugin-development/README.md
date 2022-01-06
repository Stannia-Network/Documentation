---
description: >-
  Most of our libraries are kept open source and free to use entirely. We want
  to provide a good foundation for our own plugins as well as open for the
  possibility for others as well.
---

# Plugin Development

We mainly write everything using [Kotlin ](https://kotlinlang.org)and [Gradle](https://gradle.org). If you're a developer looking to use our libraries for your own plugins, it's highly recommended that you also write [Kotlin](https://kotlinlang.org), not everything will be directly supported in Java.

If you insist on writing in Java, there are probably more compatible libraries for you to use.

### Server Compatibility

| Initial Version | Minecraft 1.18                                                  |
| --------------- | --------------------------------------------------------------- |
| Tested Servers  | [Paper](https://papermc.io), [Spigot](https://www.spigotmc.org) |
| Tested Versions | 1.18                                                            |

## Features

* Basic Plugin Handling
  * Plugin Base to extend, instead of JavaPlugin
  * Handles saving and loading automatically
    * You need to override the save and load method (if your plugin needs them), the library (sadly) can't automatically figure out the save/load logic for your plugin.
  * Convenient resource saving (move resources from plugin jar to plugin's data directory)
  * Global JSON and YAML mappers using [Jackson](https://github.com/FasterXML/jackson)
    * Makes it very easy to parse any YAML or JSON config/data
  * Handles server reloading
    * If needed, you can override `onReload()` to add additional logic to the server reload command.
* General Command Library
  * Helps you implement commands in a more convenient way
  * Supports sub commands
  * Supports tab completion
* Message/Text Translation
  * All of your plugin messages or text can support translations
* Player Settings
  * Easy to use player settings
  * Default Value(s)
    * Server owners can override default value(s) from config
  * Server owners can limit certain values or value ranges to certain permissions
  * Player commands provided by the library, no need to implement any commands
* Player Flags
  * Easy to use player flags
  * Default state (whether to default enable or disable)
    * Server owner can override from config
  * Player commands provided by the l ibrary, no need to implement any commands
* Message Building
  * Supports building messages using chat components (for clickable links, tooltips etc), which can be used both in chat and books
  * Cooldown between sending
  * Prefix (defaults to the one configured in **StanniaLibrary**
  * Position (Chat, ActionBar, Title etc)
  * Translations (see [Translations](../translations.md))
  * Placeholders
* Book Building
  * Custom books, for stuff like help descriptions on various things.
  * Translations (see [Translations](../translations.md))
  * Gives a player said book in given circumstance
    * Circumstance can be by command execution, death, (first) login etc
  * Supports components just like game chat (hover tooltips and clickable links etc)
* Event System
  * Implement custom events easily
  * Event manager that will register the events for you conveniently
* Various Extension & Utility Functions
  * Using Kotlin for extension methods to make code nicer and shorter
  * Some of the implemented extension methods are:
    * \`UUID.getWorld()\` -> get World by UUID instance
    * \`UUID.getPlayer()\` -> get Player by UUID instance
    * \`UUID.getOfflinePlayer()\` -> get OfflinePlayer by UUID instance
    * \`String.toPath()\` -> Convert string to Path
    * \`String.toFile()\` -> Convert string to File

