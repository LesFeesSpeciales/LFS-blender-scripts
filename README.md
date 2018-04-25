# LFS Blender Scripts

Various Blender scripts, used in production or proof of concepts.

## Table of Contents

* [3D View](#3d-view)
  * [Image background transform](#image-background-transform)
* [Files](#files)
  * [Filesize graph](#filesize-graph)
* [Layout](#layout)
  * [Camera plane](#camera-plane)
* [Material](#material)
  * [Material tuning](#material-tuning)
  * [Proxify](#proxify)
* [Rigging](#rigging)
  * [Mesh To Bone Shape](#mesh-to-bone-shape)
  * [Tesselation](#tesselation)
* [Simulation](#simulation)
  * [Particle system template](#particle-system-template)
    * [Fourmis](#fourmis)
* [License](#license)

### 3D View
#### Image background transform
Transform 3D View background images using G, R, S, similar to Blender transform tools.
* `SHIFT` + `ALT` + `B` to start the operator, then
* `A` to transform all images at once
* `CTRL` to snap to closest values
* `X`/`Y` to constrain to axis
* `SHIFT` for precision mode
* `MOUSEWHEEL` to choose a different image

Note that the pivot mode (3D Cursor, Individual Origins, etc.) is considered during transformation, to allow precise scaling and rotating.

![Background image transform](docs/BG_xform_edit.gif "Background image transform")  

---
### Files
#### Filesize graph
This script generates a curve in the 3D view based on a file sequence present in the specified directory. It should be used to monitor image sequence rendering. It allows the user to quickly spot empty images, as well as some artifacts when an image has a different weight from its neighbors.

---
### Layout
#### Camera plane
Import an image and parent it to the camera. You can then set the distance and width from the image object's properties. The plane will adjust to the camera's FOV or focal length.  
You can easily import several images at once, which will be equally spaced in depth. This is useful when creating painted stage-like sets which need to stick to a camera.

![Plane settings](docs/camera_plane_props.png "Camera Custom Properties")  
Two settings are available upon selecting a plane:
* `distance` is the distance from the camera to the plane
* `passepartout` is an additional scale for the plane

![Focal 1](docs/camera_plane_focal1.png "Focal 1")  
![Focal 2](docs/camera_plane_focal2.png "Focal 2")  
Two focal settings with the same plane.

Please see [this article](http://lacuisine.tech/2017/10/21/cameraplane-a-tool-for-2d-sets/) for a more in-depth overview of the tool.

---
### Material
#### Material tuning
Change some material properties. Useful for recolorizing textures on multiple objects at the same time (eg. add a globally darker shade to a character in a given shot). Blender Internal only.

Internally, this add-on creates a Blender Internal shading nodetree including several filters, and exposes these filter nodes' interfaces in the Material Panel.

![Material Tuning settings](docs/material_tuning_settings.png "Material Tuning settings")  
The various parameters are simply applied from top to bottom. The `Color2` parameters sets a global hue with a factor.

You can copy the settings from the active object to selected objects.

#### Proxify
Create proxy images to enhance performance in scenes containing a large number of large textures.

---
### Rigging
#### Mesh To Bone Shape
Transfer a mesh object's shape to the active bone in Pose Mode. Automatically creates a `WGT_` object instance.

![Mesh To Bone Shape selection](docs/shape_to_bone.png "Mesh To Bone Shape selection")  
To apply a shape, select a mesh object, then the armature. In *Pose Mode*, select the bone you wish to apply the shape to. The mesh shape will be transferred to the bone in its current position.

#### Tesselation
Automatically tesselate an image plane for later skinning.  
This add-on requires [scipy](https://www.scipy.org/) and [skimage](http://scikit-image.org/), as well as [triangle](http://dzhelil.info/triangle/), available from the [pypi](https://pypi.python.org/pypi/triangle/). This library needs to be compiled against the same Python version as Blender. In Linux this may involve compiling Python, and a virtual environment. An article explaining the precess is available [here](http://lacuisine.tech/2017/10/20/how-to-install-python-libs-in-blender-part-2/), but feel free to contact us for assistance!

![Tesselation before](docs/tesselation_before.png "Tesselation before") ![Tesselation after](docs/tesselation_after.png "Tesselation after")  

---
### Simulation
#### Particle system template
An example script to create particle simulations using duplivert instances at each animation frame.

#### Fourmis
French for “ants”. Uses the particle system template to generate an ant colony walking along a specified path using boids.

-----

# License

Blender scripts shared by **Les Fées Spéciales** are, except where otherwise noted, licensed under the GPLv2 license.
