# Exporting to FBX
First of all, Unity needs the `FBX Exporter` package installed. Next, find the model to export, rightclick and choose `Export To FBX`. In the popup select `Binary` for the export format.

## Exporting animations
When exporting the FBX, make sure that these aren't checked (underneath Bake Animation):
* NLA strips
* All actions

Next in Blender choose `File | Import | FBX` to import and edit it.
## Reimporting in Unity
Select `Assets | Import New Asset` and find the fbx file. After importing make sure to uncheck `Import Cameras` and `Import Lights`.

### Reimporting animations
Underneath `Model` make sure `Bake Axis Conversion` is checked. 