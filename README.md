# Blender Wavefront OBJ Importer/Exporter

This is a modified version of the default-included OBJ exporter, which adds an option to export a vertex normal entry for every vertex, regardless if the same normal already exists.
For example, output of the old script might have
```
vn 1.0000 0.0000 0.0000
vn 0.0000 1.0000 0.0000
```
where the normals are referenced by multiple face entires.
This script will duplicate them if necessary, so there are as many `vn` entries as there are `v` entries.

## Purpose
The purpose for this is to force consistency between multiple exports of a model, where the vertices have only been moved.
This is useful for shape morphing.
In SceneKit's SCNMorpher class, without consistent normal indices, the morphing fails.

## Installing
To install, copy the `io_scene_obj_all_normals` folder into the `scripts/addons_contrib/` folder of your Blender installation.
Then it will show up in Add-ons as "Import-Export: Wavefront OBJ format - all normals".
You should disable the default OBJ importer/exporter before enabling this one, so you can differentiate them in the menu.

## Usage
The importer is completely unchanged.
The exporter is the same, except for an additional check-box titled "Write All Normals", which, when checked, will write a `vn` line for every vertex, even if the normal is the same as another vertex.

When exporting models for shape morphing in SceneKit, I have found the following settings to work.
Several more of the settings could probably be labeled (optional), but I have not tried them myself.

 - Selection Only: (optional)
 - Animation: NO
 - Apply Modifiers: (optional)
 - Include Edges: NO
 - Smooth Groups: NO
 - Bitflag Smooth Groups: NO
 - Write Normals: YES
 - Write All Normals: YES
 - Include UVs: NO
 - Write Materials: NO
 - Triangulate Faces: NO
 - Write Nurbs: NO
 - Polygroups: YES
 - Objects as OBJ Objets: YES
 - Objects as OBJ Groups: NO
 - Material Groups: NO
 - Keep Vertex Order: YES

