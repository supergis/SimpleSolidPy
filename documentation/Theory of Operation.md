Openscad is a functional language with much of it's syntax matching up to what python provides.  This module does
2 things.


1. Provides a parser that converts specific from openscad syntax into a format that python can understand.  This needs
   to do the following:
     * Mapping openscad words to python keywords.  Such as converting the module openscad statement to a
       python def statement.
     * Translating case differences.  Such as changing true to True
     * Converting { } into indents

   Simple example:
       import openscad.parser

       print openscad.parser.openscad_string('''
       module foo() {
           cube([10,10,10], center=true)
       }
       ''')

       Returns
       def foo():
           openscad.functions.cube([10,10,10], center=True)

2. Provides a wrapper that implements the openscad functional statements using the Freecad python api.  So for example
   it provides a cube() function that accepts the openscad syntax uses the Freecad modules to create the resulting
   object.

