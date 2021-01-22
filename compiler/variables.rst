Variables
=========

With the compiler, you can set compile-time variables. To set a variable, the ``_SetVariable`` element is used.
Variables are visible within the "scope" of the ``_SetVariable`` element.
This means that everything after the element and within the element's parent can use the variable. 
Setting the variable again in a child will only be effective in that child. Outside of that child, it is back to what it was. 


``%variable_name%`` is used to use a variable in an attribute or inside of an element's text value. 
Similar to global embeds, variables can be used alongside strings and other variables.
You can even use variables in the value field of ``_SetVariable`` elements. If the variable is not defined in the current
scope, the text will not change. So, if there is an attribute with value ``It is %my_variable%`` and the variable ``%my_variable%``
is not defined in the current scope, the attribute's value will stay as ``It is %my_variable%``.

.. code-block:: xml

 <Element1>
  <_SetVariable name="h" value="hh"/>
  <!-- Everything after can use the variable "h" -->
  <Element2>
    <_SetVariable name="a" value="aa"/>
    <!-- Everything after can use the variable "a" -->
    <_SetVariable name="h" value="%a%hh"/>
    <!-- "h" is now equal to "aahh" but only within Element2 -->
  </Element2>
  <!-- "h" is back to being "hh" -->
  <!-- Can no longer use the variable "a" since we are out of Element2 -->
 </Element1>

Example
-------

.. code-block:: xml

 <_SetVariable name="prefix" value="prfx"/>
 <Object type="0x0000" id="%prefix% My Item">
    <Class>Equipment</Class>
    <Item/>
    <Texture>
        <File>myTextureFile</File>
        <Index>0x00</Index>
    </Texture>
    <SlotType>10</SlotType>
    <Description>My cool item</Description>
 </Object>

What the compiler will turn the above XML into:

.. code-block:: xml

 <Object type="0x0000" id="prfx My Item">
    <Class>Equipment</Class>
    <Item/>
    <Texture>
        <File>myTextureFile</File>
        <Index>0x00</Index>
    </Texture>
    <SlotType>10</SlotType>
    <Description>My cool item</Description>
 </Object>