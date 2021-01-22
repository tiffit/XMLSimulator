Loop Block
==========

The ``_loop`` element can be used to repeat XML and incrementing a variable before each repetition.
The ``variable`` attribute is the variable that should be incremented. This variable is set to ``start`` and
the XML will be repeated (``end`` - ``start`` + 1) times. So, with a ``start`` value of 1 and ``end`` value
of 10, the XML will be repeated 10 times and the variable will go from 1 to 10.

Example
-------
.. code-block:: xml

 <_loop variable="i" start="1" end="3">
    <Behavior type="auto" projectileId="%i%" defaultAngle="_eval(%i% * 45)">Shoot</Behavior>
 </_loop>

The compiler will turn the above XML into:

.. code-block:: xml

 <Behavior type="auto" projectileId="1" defaultAngle="45">Shoot</Behavior>
 <Behavior type="auto" projectileId="2" defaultAngle="90">Shoot</Behavior>
 <Behavior type="auto" projectileId="3" defaultAngle="135">Shoot</Behavior>

