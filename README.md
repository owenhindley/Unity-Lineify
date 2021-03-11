# Unity-Lineify
Houdini + Unity tool to export line-based meshes from Houdini using CSV.

Background:
This tool will allow you to export geometry from Houdini into Unity, and have them represented as MeshTopology.Lines (GL_LINES). This expects pairs of mesh indices, rather than trios of triangle indices, so we can't use FBX directly (I guess you could have a custom importer for FBX..). Lines have a few advantages over triangles for particular visual effects, such as remaining single-pixel width at a distance (and therefore differently resistant to aliasing problems), and are super useful + visually interesting in certain situations :)

Be warned, you will likely need to experiment a bit with your input geometry in Houdini before feeding it to this HDA (for example using the Convert Line SOP) to get the results you're after.

Nice things to try:
- Normals are exported, so you can acheive fresnel-style effects on wireframes
- UVs are exported, which combined with moving textures can make for some cool crawling / traffic-at-night-from-a-distance effects.

### Dependencies

This HDA requires 'AutoUV' from the SideFX Labs toolset, which you can download here :  https://github.com/sideeffects/SideFXLabs. Optionally you can open up the HDA and remove this dependency.

### Instructions

1) In Houdini, install Export To CSV HDA via Asset Manager
2) The HDA operates on vertices. It will automatically add normals and UVs if needed, using the SideFX Labs 'AutoUV' node.
3) It then exports a CSV file to the specified location in the Parameters Window when you press Export. It's helpful to export this file directly into your Unity project.

4) In Unity, you should be able to import this folder as a Package via PackageManager.
5) The CSV file you exported should appear as a TextAsset. You can then open the EditorWindow (Window -> LineMeshFromCSV).
6) Select the source CSV file, click 'Make Mesh'
7) The routine should create a new Mesh Asset in the same folder as the CSV file.

Enjoy!

