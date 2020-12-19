Usage
======
*Fast Events* has a number of action- and filter hooks that can be used to inject custom specific code. Take a look at the examples paragraph of the functions to get an idea how to use them.

If you want to use the filter and action hooks, there are generally a few options.

#. You add your code to the ``functions.php`` file of your theme. The downside of this approach is that every time your theme gets an update you have to redo your changes.
#. Add it to a function in a child theme. This way you don’t have to redo your code if the theme gets an update, but it requires more knowledge.
#. Write you own plugin. You have to be a seasoned developer to go down this path.
#. Or…. use a plugin that does most of the magic for you. If you just want to use a limited set of filters and or action hooks we strongly advice you to take this route. Install the `Code snippets <https://wordpress.org/plugins/code-snippets/>`_ plugin. All the examples in the functions can be easy copied into ``Snippets`` of this plugin. Most examples are easy to understand and easy to adjust.

.. tip:: If you have made a nice snippet yourself, let us know, and we will include it in the documentation as an example.
