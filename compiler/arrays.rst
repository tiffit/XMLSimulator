Arrays
======

Arrays are a way to store multiple values in a single variable. The ``_SetArray`` element is used to set an array
element with comma separated values. 

.. code-block:: xml

 <_SetArray name="colorNames" values="Red,Maroon,Magenta,Purple,Blue,Light Blue,Teal,Green,Dark Green,Yellow,Orange,Brown,Black,Gray,Light Gray,White"/>

Values of the array can be retrieved using the ``_GetArray`` element. The ``index`` attribute is the index of the array
to retrieve the value from. It is important to note that the index for arrays begin at 1. The ``variable`` attribute is the
variable to store the value to.

.. code-block:: xml

 <_GetArray name="colorNames" index="1" variable="color"/>

Example
-------

.. code-block:: xml

 <_SetArray name="angles" values="0, 5, 10, 15, 44"/>
 <_loop variable="i" start="1" end="5">
    <_GetArray name="angles" index="%i%" variable="angle"/>
    <Behavior type="auto" projectileId="%i%" defaultAngle="%angle%">Shoot</Behavior>
 </_loop>

What the compiler will turn the above XML into:

.. code-block:: xml

 <Behavior type="auto" projectileId="1" defaultAngle="0">Shoot</Behavior>
 <Behavior type="auto" projectileId="2" defaultAngle="5">Shoot</Behavior>
 <Behavior type="auto" projectileId="3" defaultAngle="10">Shoot</Behavior>
 <Behavior type="auto" projectileId="4" defaultAngle="15">Shoot</Behavior>
 <Behavior type="auto" projectileId="5" defaultAngle="44">Shoot</Behavior>