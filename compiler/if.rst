If Block
========

The ``_if`` element can be used to include or exclude a set of elements based on a given condition. All child elements
of the ``_if`` element will only be included if the given condition is true.

If statements are best used in global embeds and include files where variables and parameters can change.

Example
-------
.. code-block:: xml

 <_if condition="%myVariable% > 2">
    <Texture>
        <File>myTextureFile</File>
        <Index>0x05</Index>
    </Texture>
 </_if>
 <_if condition="%myVariable% &lt;= 2">
    <Texture>
        <File>myTextureFile</File>
        <Index>0x04</Index>
    </Texture>
 </_if>

If the variable ``myVariable`` is greater than 2, the compiler will turn the above XML into:

.. code-block:: xml

 <Texture>
    <File>myTextureFile</File>
    <Index>0x05</Index>
 </Texture>

Otherwise, the compiler will turn the above XML into:

.. code-block:: xml

 <Texture>
    <File>myTextureFile</File>
    <Index>0x04</Index>
 </Texture>
