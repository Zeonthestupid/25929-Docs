Base Modules
============

All of the base modules contain minimal decoration, and are optimized for large use. They get placed directly onto the menu.

Most of the base modules have three different ways of getting the current value of the item (excluding action, which doesn't have anything to return)

1. When you create the menu item, save it as a variable rather than a lambda, and call ``getValue()`` directly on the class.
2. On any display buffer, call ``getValue(index)`` to get the value in said index.
3. For bulk reads of the whole buffer, you can instead call ``getItems()`` to return a list of tuiModules.



------
Action
------

Actions are menu items that allow you to run functions when pressed.

.. code-block:: java

    new Action("StopRobot", this::requestOpModeStop)

You may use any function as long as it is a Runnable.



-------
Classic
-------


In order to use standard telemetry alongside menus, you can use the classic tuiModule.

.. code-block:: java

    new Classic("Hi I display a line")
    new Classic("I display a line", "with data!")

Classic modules allow you to both display lines, and display them alongside data. Extend features of classic telemetry, data will automatically use the built in ``.tostring()`` to convert ints, floats and anything else into a displayable string.

    ⚠️ If you need to use only ``Classic`` Modules within a buffer, make sure to set the third argument to false ``new Classic("Hi", "", false)`` ,  which overrides the skip functionality to prevent an overflow error.




------
Toggle
------

Toggles are menu items that act as booleans, allowing you to toggle a parameter off and on. By default, you use two different names for on/off. As this is a base module, there is no extra decoration or indicators on whether the module is on or off.


.. code-block:: java

    new Toggle("NameWhen0", "NameWhen1", 1)

Toggles start with a state denoted as the third argument.

The ``getValue()`` method of the toggle returns the current state (as a Boolean)




--------
Dropdown
--------

Dropdowns are menu items that allow you to select an item out of a list. They are useful to build when you need someone to select an option, but still want to keep it generally readable. Only one item is able to be selected, and when getting the value of the class, will return a string of the list item.

.. code-block:: java

    new Dropdown("DisplayName", "op 1", "op 2")

Dropdowns allow you to use as many options as you want. However, you may want to consider using a smaller amount of items.

The ``getValue()`` method of the dropdown returns the current option as a string




--------
Modifier
--------

Modifiers are menu items that allow you to change a value by a certain amount. You can define both the value and amount by

.. code-block:: java

    new Modifier("DisplayName", 2, 5)

The second parameter (2 in this case) defines the starting value, and the third parameter (5 in this case) defines how much to increase it by when the user clicks up.

The ``getValue()`` method of the dropdown returns the current value

