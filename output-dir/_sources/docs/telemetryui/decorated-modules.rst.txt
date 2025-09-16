Decorated Modules
=================


Only some of the base modules appear as decorated modules, as decorated modules inherit general UX design principles that some of the base modules lack.

Like with the base modules you may call ``getValue()`` on the class or ``getValue(index)`` / ``getItems()`` on the display buffer.


------
Toggle
------

The decorated toggle functionally acts the same, however, instead of just an on/off name, there is also an additional switch like indicator.

T

Refer to the previous Toggle module for usage


--------
Dropdown
--------

Dropdowns within the decorated modules work slightly differently, showing a full list of the options when clicked. This means that you should take caution in creating long lists, as they may get cut off.

By clicking on the dropdown the first time, it will open up the list, and the second time will close it, selecting the item you picked.