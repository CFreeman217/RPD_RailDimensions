# RPD_RailDimensions
Dimension Railings In a revit view

1. Choose all elevation views of type "Rail Elevation"
2. Find all railings in view
3. Copy the railing geometry, convert the copy to detail lines
4. Dimension both ends and sloped section
  - Add notes for F.V. and EXT.
5. Find floor and stair elevation
6. Draw a white shaded region to fit the riser/landing profile
  -? Set view settings for all other components of stair to be transparent
  -? Where is the bottom of this shaded region
7. Place tag with rail name on rail in view.
8. Assign this command to a button in the pyRevit console.


Name railings based on placement: With rooms defined, as railings are placed, they get numbered based on type, room name, and placement order. Append this string to the "Mark" parameter for tagging.
The rail schedule must get updated as railings are placed on sheets. Generate default descriptions and elevation callout tag to automatically populate the schedule.
