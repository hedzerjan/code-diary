# Understanding Flexbox
Terms: Container, Item, Main axis, Cross axis, Flex direction
Item can also be a container

## Default behaviour
For the main axis: take up the space you need but no more
For the cross axis: take up as much as possible
## Justify content
Is about the main axis and where the elements end up:
* start: start of the main axis
* center
* end
## Align content
Is about the cross axis and what the content should do. Start, center and end are obvious. Stretch is important, it takes up space and enables justify content.
## Flex
Basis, Shrink and Grow work together as a unity.
Size along the main axis? But then a sort of minimum size desired, not wanted, cause it can shrink. Ideal size may be better. But it depends on its shrink setting, shrink 0 means a hard ideal size.
Flex basis in % means the % of space that the parent gives us. So prefer to use % unless using pictures that have a fixed size. 
Flex basis Auto means look at the space you need for your content. This is not everything however, it also looks at all the competing elements.
Flex basis 0% seems to mean take as much space as you want.
## Position
Using relative position with top/bottom/left/right means it will keep taking up the original space in the flexbox system but then the display of the element will be shifted.
Absolute position makes the element leave the flexbox system.