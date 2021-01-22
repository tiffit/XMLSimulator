Including Files
===============

Using the ``_Include`` element, you can include other XML files in the current XML file. ``_Include`` elements
are processed first by the compiler before it does anything else. Think of these like embeds but for files. 
Everything from the other file (excluding the root element) is copied into where the include element is.

Included XML files can't have ``_Include`` elements of its own. The root element of the include file 
can be called anything but must have the ``include="true"`` attribute.

Example
-------
"someoneObjects.xml":

.. code-block:: xml

 <Objects>
    <Object type="0x0001" id="My Reusable Item">
        <_Include name="reusableItem.xml"/>
        <Texture>
            <File>myTextureFile</File>
            <Index>0x00</Index>
        </Texture>
        <Description>This item can be reused many times!</Description>
        <feedPower>2</feedPower>
        <BagType>6</BagType>
    </Object>
 </Objects>

"reusableItem.xml":

.. code-block:: xml

 <ThisCanBeCalledAnythingItDoesntMatter include="true">
    <Class>Equipment</Class>
    <Item/>
    <InvUse/>
    <SlotType>10</SlotType>
    <DropTradable/>
 </ThisCanBeCalledAnythingItDoesntMatter>

What the compiler will turn "someoneObjects.xml" into:

.. code-block:: xml

 <Objects>
    <Object type="0x0001" id="My Reusable Item">
        <Class>Equipment</Class>
        <Item/>
        <InvUse/>
        <SlotType>10</SlotType>
        <DropTradable/>
        <Texture>
            <File>myTextureFile</File>
            <Index>0x00</Index>
        </Texture>
        <Description>This item can be reused many times!</Description>
        <feedPower>2</feedPower>
        <BagType>6</BagType>
    </Object>
 </Objects>