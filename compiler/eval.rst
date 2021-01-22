Evaluation
==========

Surrounding an attribute value or text value in ``_eval()`` will cause whatever is inside to be evaluated. Unlike variables,
the ``_eval()`` can't be surrounded by any strings. Thus, something like ``_eval(5+3) is a number`` wouldn't evaluate. To get
around this, you can evaluate to a variable then use the variable later on like so:

.. code-block:: xml

 <_SetVariable name="evalResult" value="_eval(%variable% * 3)"/>
 <Behavior type="auto" projectileId="1" defaultAngle="3%evalResult%">Shoot</Behavior>
