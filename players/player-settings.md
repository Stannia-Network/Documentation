---
description: >-
  Servers using plugins depending on our libraries, or our official plugins will
  all be able to implement settings that you can configure for yourself via
  commands.
---

# Player Settings

### Commands

_\[]: Optional Argument_ | _<>: Required Argument_

#### /settings \[SEARCH\_TEXT]

Will give you all settings completely or partially matching **SEARCH\_TEXT**.

Mousing over the setting names in the list you get in return will give you a tooltip with it's description.

Clicking a setting name in the list you get in return will send you another message with that setting's value.

#### /setting \<SETTING\_NAME> \[OPERATOR] \[VALUE(S)]

Will get current value or set new value(s) for **SETTING\_NAME**.

* If only setting name is provided, will give you the current value of the setting.
* If setting is a list type, it can have an operator (will be suggested while typing) for adding or removing from the current list of values.
* Can take a single word/number value or comma/space separated values.
  * _/setting setting-with-list-values + VALUE1, VALUE2, VALUE3_ - Will add to the current list of values.
  * _/setting setting-with-list-values - VALUE1, VALUE2_ - Will remove from the current list of values.
  * _/setting setting-with-list-values VALUE1 VALUE2 VALUE3_ - Will override the current value.

