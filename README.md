# FreeCAD Example: Dynamic Linked Object

Link (internally `App::Link`) is an important new feature introduced in FreeCAD 0.19 assemblies.

This repository aims to layout one pattern for complex assemblies involving *dynamic linked objects* which aims to reduce duplication of assembly related logic such as orientation, positioning, or number of instances.

## Example
To illustrate the dynamic linked object concept, consider a table with four legs.

Each leg has two different variants:

* Round
* and Square

The variants can be controlled by a parameter in a spreadsheet.

For our table model, we'll create '''five''' separate documents:

1. `TableTop.FCStd` - containing the top of the table.
2. `RoundTableLeg.FCStd` - containing a ''round'' table leg.
3. `SquareTableLeg.FCStd` - containing a ''square'' table leg.
4. `Table.FCStd` - containing the assembly of the table top and legs.
5. `Spreadsheet.FCStd` - containing a spreadsheet to drive the model.

Our simple table model will define the following parameters in `Spreadsheet.FCStd`:

1. `TableTopSize` - Dimension of the **square** table top.
2. `TableTopThickness` - Thickness of the table top.
3. `TableLegSize` - Size of each table leg. For Square leg, this is the dimension. For Round leg, this is the diameter.
4. `TableLegHeight` - Height of each table leg.
5. `TableLegVariant` - Controls the style of table leg. Possible values include "`Square`" and "`Round`".

`Table.FCStd` is where the dynamic linked object concept is illustrated.

The goal is to *not* duplicate the following assembly logic for each table leg variant:
* Each table leg must appear **four** times underneath each corner of the table top.

![Dynamic Table Leg](dynamic-table-leg.gif)

## See Also
https://wiki.freecadweb.org/Dynamic_linked_object