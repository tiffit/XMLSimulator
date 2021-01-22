Global Embeds
=============

Global embeds function similarly to normal embeds but are for the entire XML file. 
GlobalEmbeds aren't just for behaviors either, they can work for anything. 
You can put an entire object in a global embed and change values using parameters. 
In addition, parameters work the same way as regular XML except you can combine strings and parameters. 
For example, you can have an attribute that looks like ``name="{param1} is a {param2}""``.

The ``_DefineGlobalEmbed`` element is used to define global embeds and the ``_GlobalEmbed`` element is used to
include a global embed where the current element is. ``_DefineGlobalEmbed`` *must* be defined at the top level.
That is, it must be a direct child of the root element. The actual position of the element does not matter
as long as this condition is met.

Global embeds can be thought of similarly to ``_Include`` elements. Unlike ``_Include`` elements, global embeds
can be parameterized and nested. This means that you can have one global embed inside of another.

Example
-------
Define Global Embed:

.. code-block:: xml

 <_DefineGlobalEmbed name="Shoot Projectile with Offset">
    <Behavior projectileId="0" numShots="1" posOffset="{xOffset},2">Shoot</Behavior>
 </_DefineGlobalEmbed>

Object:
 
.. code-block:: xml
 
 <Object type="0x0001" id="My Cool Enemy">
    <Class>Character</Class>
    <Texture>
        <File>myTextureFile</File>
        <Index>0x00</Index>
    </Texture>
    <Enemy/>
    <Projectile id="0">
        <ObjectId>My Object</ObjectId>
        <Speed>10</Speed>
        <Damage>10</Damage>
        <LifetimeMS>500</LifetimeMS>
    </Projectile>
    <_GlobalEmbed name="Shoot Projectile with Offset"/>
        <Param name="xOffset">3</Param>
    </_GlobalEmbed>
 </Object>

What the compiler will turn the object into:

.. code-block:: xml
 
 <Object type="0x0001" id="My Cool Enemy">
    <Class>Character</Class>
    <Texture>
        <File>myTextureFile</File>
        <Index>0x00</Index>
    </Texture>
    <Enemy/>
    <Projectile id="0">
        <ObjectId>My Object</ObjectId>
        <Speed>10</Speed>
        <Damage>10</Damage>
        <LifetimeMS>500</LifetimeMS>
    </Projectile>
    <Behavior projectileId="0" numShots="1" posOffset="3,2">Shoot</Behavior>
 </Object>

