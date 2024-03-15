# UI Toolkit basics
## Position
When choosing positioning `relative` it actually means that Flex is in control of positioning. `Absolute` means that you are completely in control, even putting the element on top of others.

## Shrink/grow
If `shrink` is non-zero, Flex is allowed to shrink it when needed.

Grow is the opposite, grow zero means no growing when there is space.

## Display
Display removes the element from the hierarchy. The good thing is this allows elements underneath mouse access but the bad thing is it cause Flex to reallign stuff.

## Scripting
UI Toolkit is separate from the rest of the engine. So the cohesion is loose. To access the ui from script start with
```c#
GetComponent<UIDocument>().rootVisualElement
```
From then on you can access this root and query for other elements by name:
```c#
root.Q<VisualElement>("element-name");
```
And influence them for example:
```c#
element.style.display = DisplayStyle.None;
```
### Changing classes
```c#
element.AddToClassList("classname");
```

## Events
To influence scripts from the UI you use events:
```c#
button.RegisterCallback<ClickEvent>(MethodName);
```
And then the handler:
```c#
private void MethodName(ClickEvent evt)
```

## Animation
Animation is all done through Transition Animations. Then if moving items, prefer the Transform > translate property. 

### Looping animation
Toggle the class that triggers the animation, and then register for the event that signals the end of the animation, like this:
```c#
elem.ToggleClassList("style-name");
elem.RegisterCallback<TransitionEndEvent>
(
    evt => elem.ToggleClassList("style-name")
);
```
