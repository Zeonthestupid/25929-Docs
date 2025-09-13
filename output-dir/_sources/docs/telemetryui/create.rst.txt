Creating Your Own Modules
=========================

To create your own module, first create a class that extends ``tuiModule``. Then, make sure to construct the module for any parameters needed.

For this, we'll create an Action (the simplest base module)

.. code-block:: java
    public Action extends tuiModule() {
        private final Runnable function;
        private final String displayName;

        public Action(String display, Runnable function) {
            this.function = function;
            this.displayName = display;
        }

    }

``tuiModule`` has many classes you can override, each with different functionality, however, you must extend a display class or nothing will display

    public void onRight() {}
    public void onLeft() {}
    public void onUp() {}
    public void onDown() {}

    public void onEnter() {}
    public void onExit() {}

    public void onClick() {}




    public boolean inputReleased() {return true;}


    public String display() {
        return "DisplayNotOverridden.";
    }

    public List<String> mldisplay() {
        return null;
    }


    public Object getValue() {
        return null;
    }

