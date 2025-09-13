Getting Started
===============


TelemetryUI is split into four different sections:

- **Core modules** (Which makeup the functionality and must be imported in any project using TUI)

- **Base modules** (Which makeup the base actions of menus such as the ability to run functions, change parameters and more)

- **Decorated modules** (Which are base modules with extra **flair**)

- **Wrapped modules** (Which are ways to wrap other modules into things like columns and more)

----------
Base Usage
----------
The example usage of telemetryUI lib is as follows:

.. code-block:: java

    List<tuiModule> display01;
        displayBuffer db = new displayBuffer("0. Main Menu");
        displayManager displaymanager = new displayManager(telemetry, gamepad1);

        @Override
        public void init() {
            display01.add(new Action("StopRobot", this::requestOpModeStop));
            displaymanager.loadBuffer(db);
            mainmenu.setItems(display01);
        }

        @Override
        public void loop() {
            displaymanager.update();

        }



**Breakdown**
To start a telemetryUI project, you must first import the **core modules**:

.. code-block:: java

    import telemetryui.core.*

After such, you must initiate a ``displaymanager`` class

.. code-block:: java

    displayManager dm = new displayManager(telemetry, gamepad1);

In order to display things on the manager, you must create a ``displayBuffer``. ``displayBuffer`` s are created as such

.. code-block:: java

    displayBuffer db = new displayBuffer("menuName")

Keep in mind the ``menuname`` WILL be displayed on the top of the menu.

After, create a list of ``tuiModule`` s. Everything that displays within a menu inherits the tuiModule class.

.. code-block:: java

    List<tuiModule> display01;



------
TUI V2
------






