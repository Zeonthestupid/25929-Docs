Creating Your Own Modules
=========================


To create your own module, first create a class that extends ``tuiModule``. Then, make sure to construct the module for any parameters needed.

There are many different methods you may override, each with their own respective functionality. The list with a quick description is as follows (but read through the full page if you ever feel confused)


**Required(mostly)**

    | display() // Returns a string of what to display
    | getValue() // Returns the selected value (can be any object)


**Inputs:**

    | onRight() // Returns Void, run whenever the right d-pad is clicked
    | onLeft()  // Returns Void, run whenever the left d-pad is clicked
    | onDown() // Requires input release to be activated, returns void, run whenever the down d-pad is clicked
    | onUp() // Requires input release to be activated, returns void, run whenever the up d-pad is clicked
    | onClick() // Returns Void, run whenever the A button is pressed


**Additional Usage:**

    | inputReleased() // Returns a boolean on whether to allow up/down for menu.
    | mldisplay() // Returns a list of Strings. When not null, multi-line displaying is active.
    | isSkipping() // Returns a boolean on whether to skip the module when going through the lists.









-----------
Basic Usage
-----------

For the first part of this, we'll create an Action (the simplest base module)

.. code-block:: java

    public Action extends tuiModule() {
        private final Runnable function;
        private final String displayName;

        public Action(String display, Runnable function) {
            this.function = function;
            this.displayName = display;
        }

    }


All modules contain a constructor of inputs to determine how things are displayed. In the context of an ``Action`` this means taking in a runnable, and a string.

TuiLib works by always returning the ``display()`` method of each ``tuiModule`` inside of the buffer, creating what's shown. It's important to create a ``display()`` method that reflects how people should interact with it.
In the case of actions, the ``display()`` method is as follows:

.. code-block:: java

    @Override
    public String display() {
        return displayName
    }

This works well, however, there is no way to run the function yet. In order to run it, you may override the ``onClick()`` method.

.. code-block:: java

    @Override
    public void onClick() {
        function.run();
    }

You most likely want more than just actions, so here's the rest of the basic functions:

In order to return a usable value for your code, you can use the ``getValue()`` method, so long as it returns the object type of your returning value. Refer to the base modules page if you're confused on what this means.

If you want to have different things activate when you click L/R, you may use the ``onLeft()`` or ``onRight()`` methods respectively.

If for some reason you'd like to skip the module entirely (for example a custom display), you may return ``true`` with the ``isSkipping()`` method




------------------------
Utilizing Up/Down Inputs
------------------------

By default, the up and down buttons on the D-Pad move between different menu items. A lack of up / down keys however, can be limiting towards advanced usage. You may want to use these to increase / decrease a given value.

In order to use the ``onUp()`` or ``onDown()`` methods, you must override the ``inputReleased()`` class to return ``false`` , which now restricts the up / down keys, and means that the user cannot move between menu items. Be cautious of this!

As long as ``inputReleased()`` returns ``false`` you are free to use the dpad buttons to run different things.




---------------------------
Utilizing MultiLine display
---------------------------

By default, all modules utilize the ``display()`` method to return a string of what should be displayed. However, this on its own is limited for more advanced usage, such as displaying things over multiple lines.

In order to interface with the multi-line display you must override the ``mldisplay()`` class. By default, this class returns null, signifying to the displayManager that it should use the regular ``display()`` method. As long as ``mldisplay()`` is not null, it will use multi line displays.

To use multi line displays, simply return a list of Strings, where each item in the list is its own respective line.

