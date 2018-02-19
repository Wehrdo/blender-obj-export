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

