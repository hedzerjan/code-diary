# Animating in Blender
Some animations kan be done in Unity but the more complex ones require Blender. By default you can animate location, rotation and scale of an object. 

To start of select the Animation workspace and then make sure the second timeline hidden beneath de dopesheet is visible.

Next create keyframes by:
- selecting a frame in the timeline;
- changing your object;
- hovering your mouse over the object and hitting `i` to create a keyframe;
- ad infinitum.

## Animating part of an object
This is done by using `shape keys`, the shape key panel is hidden in the data properties.

First, in object mode, create a shape key with the + sign. This will be the default pose. Next, create another key and make sure it's seleted, switch to edit mode and change your object. When you leave object mode it seems as if your edits have been undone but you can use the shape keys value to see the changes.

To create an animation with these shape keys:
1. Make sure the second timeline hidden beneath de dopesheet is visible and select frame 1. Next, (make sure your shape key's value is 0) hover your mouse over the value 'slider' and hit `i`.
2. Move the frame to another part of the timeline. Change the shape key's value to 1 and hit `i` to create the next keyframe.

And that's it.