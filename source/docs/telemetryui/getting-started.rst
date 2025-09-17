Getting Started
===============

To use TelemetryUI, use the D-pad keys plus the A button!


TelemetryUI is split into four different sections:

- **Core modules** (Which makeup the functionality and must be imported in any project using TUI)

- **Base modules** (Which makeup the base actions of menus such as the ability to run functions, change parameters and more)

- **Decorated modules** (Which are base modules with extra **flair**)

- **Wrapped modules** (Which are ways to wrap other modules into things like dropdowns and columns)


In order to add an instance of telemetryUI to your opMode, you may use the sample code below:

.. code-block::

    import telemetryui.core.*;

        List<tuiModule> display01 = new ArrayList<>();
        displayBuffer mainmenu = new displayBuffer("0. Main Menu");
        displayManager displaymanager;

        @Override
        public void init() {

            displaymanager = new displayManager(telemetry, gamepad1);
            display01.add(new Action("Stop Robot", this::requestOpModeStop));
            displaymanager.loadBuffer(mainmenu);
            mainmenu.setItems(display01);

        }

        @Override
        public void loop() {
            displaymanager.update();
        }


-----------------
Understanding TUI
-----------------


TelemetryUI is split into three hierarchical levels:

1. ``DisplayManager``
2. ``DisplayBuffer``
3. ``Modules``

``DisplayManager`` is what controls inputs, creates the telemetry lines, and wraps the whole system. To create a menu, load a propagated ``displayBuffer`` into the ``displayManager`` by calling the ``.loadbuffer()`` method.

``displayBuffer`` is what holds all the modules / lines. It contains many helpful methods, that are most commonly used by the ``displayManager`` . However, you are able to use commands such as ``.updateItems()`` to interface on the buffer level.

``Modules`` are lines within the menus. They function similar to ``telemetry.addData()`` in that they are their own respective line. Modules can be split up into three different times.

Unlike many other display libraries, you do not need to unload a buffer while changing the contents.


--------------
Creating Menus
--------------

To create a menu, start by forming a new ``displayBuffer``. You may then call the ``.add()`` method, or ``.set()`` / ``.update()`` methods to add one module, or override the list respectively. Internally, ``displayBuffer`` contains a list of ``tuiModules`` ; a class that's extended by all of the modules.

You may use any combination of `base`_ , `decorated`_ or wrapped modules within your menus.

.. _base : base-modules
.. _decorated: decorated-modules