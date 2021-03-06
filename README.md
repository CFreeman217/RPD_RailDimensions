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

Select a rail and click a tool ribbon button to generate a rail elevation that frames the rail around the viewport. This might also be where we can define the flooring and stair blocking to make these drawings look good.

Steps:

1. Use the revit element view generation template from DYNAMO to trigger a section view to get cut. Use appropriate offsets and view settings to get the railing to show up in the view.
  - Later add option to decide what sheet to apply the view to. This will involve dynamic adjustment of view boundary lines and sections. 
  - Possibly add a button that allows dragging and dropping of views not assigned to sheets.
  
Problems:
1. We need a way to generate a detail line from the railing geometry on the top rail in an elevation view. Dynamo has a node that will yield a dimension given a detail line, or it is possible to generate a dimension given two points. Both of these options are preferable because the actual model space may contain a railing with a shorter or longer landing than the rail that should be installed. This is a result of the wonky railing tool native to revit. Another option may be to convert all of these items to lines to allow greater flexibility in user input. This conflicts with problem #5. Another option may be to place pipes or pipe placeholders if working with those families might be easier.
  - It might be possible to have the user draw these lines instead of needing to place tiny dots along the rail surface.
  - A tool for drawing a detail line given points exists, but then we would need a way to isolate the extreme left most, top most, and right most points from the rail to determine where to place each dimension. At this point, I have not been able to find a way to generate the points to be used as a reference.
  https://revitbeyondbim.wordpress.com/2017/02/10/element-view-generation-in-revit-with-dynamo-revised/
  
2. So far, I have not been able to isolate only the TYPE: 'Rail Elevation' from VIEW: 'Elevation' objects.

3. I can select all railings, but I will need to probably isolate the individual railing within the individual viewport to try to detect the length and geometric parameters for each situation.

4. There must be a way to trigger the dimensioning macro, and I don't want the user to have to spend too much time on the view once it is set. This means that upon view creation, the depth, width, height is all determined based on the rail geometry and it is automatically hidden with the rest of the rail views for the project. 

5. These railing elevation views must be able to adapt to changes in floors, stairs, and railings. 
