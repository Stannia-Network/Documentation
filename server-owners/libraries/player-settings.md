---
description: >-
  Plugins using our libraries can add their own settings for players to
  configure. These settings have a hardcoded default value, but you can override
  the default value by config.
---

# ⚙ Player Settings

Our settings system is quite complex and flexible, but also easy to use and configure, both for you as a server owner and for your players.

### Permission Values

You can configure certain values to be available only for those with certain permissions. These will be: `stannia.setting.<SETTING_NAME>.values.<CUSTOM_VALUE_PERMISSION>`

#### Number Value Setting Example:

This example will have following permissions:

* stannia.setting.<mark style="color:blue;">**some-setting**</mark>.values.<mark style="color:blue;">**regular**</mark>
* stannia.setting.<mark style="color:blue;">**some-setting**</mark>.values.<mark style="color:blue;">**vip**</mark>
* stannia.setting.<mark style="color:blue;">**some-setting**</mark>.values.<mark style="color:blue;">**staff**</mark>

{% code title="settings.yml" %}
```yaml
---
- some-setting
    default: 30
    permission-only-values:
        regular:
            min: 5
            max: 10
        vip:
            min: 5
            max: 40
        staff:
            min: 5
            max: 150
```
{% endcode %}

You can set min and max number for certain permissions.

* No `min` provided defaults to `0`
* No `max` provided defaults to `Integer.MAX_INTEGER` (`2,147,483,647`)
