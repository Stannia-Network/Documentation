---
description: >-
  A lot of plugins use some kind of way for players to configure options. For
  this we've created a generic way of implementing such settings. These are
  enum-based.
---

# Player Settings

### Features

* Default value(s)
* Multiple types of setting types
  * Can be lists, text, numbers, decimals and anything else really
* Supports custom tab completer
  * Default is not to suggest any values, unless it's a list type. For list type, it will suggest operators for adding or removing values.
* Supports custom value parsing
  * Default is to parse to a String
* Generic commands to lookup available settings as well as chat message click/hover actions.
  * See [Players - Player Settings](../players/player-settings.md) for more details on these commands.

#### Code Example

{% code title="DurabilityControlPlugin.kt" %}
```kotlin
@PluginMain
class DurabilityControlPlugin : PluginBase() {

    override fun onEnable() {
        super.onEnable()

        // You need to register your settings to the settings manager.
        // This is necessary in order for the generic player commands etc to work.
        settingsManager().register(
            DurabilityControlSetting.WARNING_THRESHOLD,
            DurabilityControlSetting.TOOLS_TO_CHECK
        )
    }
}
```
{% endcode %}

{% code title="DurabilityControlSettings.kt" %}
```kotlin
enum class DurabilityControlSetting(
    override val identifier: String,
    override val description: String,
    override val default: Any,
    override val tabComplete: KFunction5<String, List<String>, Player?, PlayerSetting, Operator?, List<String>>? = null,
    override val valueParser: KFunction1<String, Any?>? = null
) : PlayerSetting {
    WARNING_THRESHOLD(
        identifier = "durability-warning-threshold",
        description = "When to start showing durability warning for items.",
        default = 20,
        valueParser = ::parseInt,
        tabComplete = ::exampleNumbers
    ),
    TOOLS_TO_CHECK(
        identifier = "tools-to-check",
        description = "A list of tools to check for durability.",
        default = getToolsAndWeaponsWithDurability(),
        tabComplete = ::toolCheckTabComplete,
        valueParser = ::toolCheckValueParser
    )
}
```
{% endcode %}
