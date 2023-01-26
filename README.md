# Apex Legends Auto Shader

Blender addon that auto-shades Apex Legends characters.

## How To Use
Video: https://youtu.be/p-CK_bYSK4Y

For mesh and armatures, this addon can find and import all other textures based on the auto-imported albedo texture.

`Right-click (on armature or mesh) > Apex Shader` to access the menu.

Make sure to `Apex Shader > Set Core Apex Shader blender file path` first, to use the pre-existing `Cores Apex Shader` from `Apex Shader.blend`.

## Notes
+ This will delete existing shader nodes. Should use this on newly imported models (materials).
+ FYI, This auto shader is done by getting the image directory by looking into material's `Image Texture`. Some requirements are:
  + (All armature's) mesh's active material have at least one `Image Texture` inside, and it should have a image file attached to it.
    + If there are multiple `Image Texture`, pick one randomly.
  + The `Image Texture`'s file path must be in the format auto-generated by Legion+.
    + e.g. `bloodhound_lgnd_v20_ascension_body_albedoTexture.png`, i.e. `<meshName>_<textureName>.<fileType>`
    + That means unnamed texture files (e.g. `0x53237a2cdd03344e.png`) cannot be imported this way.
  + It will search through that directory (which the image file resides in) and import all similarly-named textures.
    + e.g. `bloodhound_lgnd_v20_ascension_body_cavityTexture.png`, i.e. `<meshName>_*` in wildcard.
+ If the auto-shading failed and the shader nodes are ruined, you can add one `Image Texture` satisfying the above condition and try to shade it again.
+ Currently supported Legion-labeled textures are:
```
[O] albedoTexture
[O] aoTexture
[O] cavityTexture
[O] emissiveTexture
[O] glossTexture
[O] normalTexture
[O] specTexture
[O] opacityMultiplyTexture (ref. https://youtu.be/dMqk0jz749U?t=1108)
[X] anisoSpecDirTexture
[X] scatterThicknessTexture
[X] transmittanceTintTexture

... (there may be other textures not listed here)
```

## Installation
Should be the same as any other addons on Github. ref. [dtzxporter/io_model_semodel](https://github.com/dtzxporter/io_model_semodel)

1. Clone this repository and zip it, or just download as zip file on Github. (`Code -> Download ZIP`)
2. `Edit -> Preferences -> Add-ons -> Install..` and choose the zip file.
3. Activate the addon by checking the box. 
   + You might have to search the addon if it is not shown automatically. (by the string `apex` or `Apex Legends Auto Shader Addon`).
4. `Save Preferences`.