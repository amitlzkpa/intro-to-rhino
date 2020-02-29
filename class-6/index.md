
# Class 6

Volume editing methods and preparation of object contours for laser cutting.

- [Upload Link](https://drive.google.com/drive/folders/1BP_lOfW-gjE02VErRaeKZ5tJmhbaIWoS?usp=sharing)
- [Grasshopper File](./Countour_numbering.gh)

# Topics
```
## Volume Editing
- BoxEdit
- CageEdit
  - Bounding Box
  - Line
  - Rectangle

## Preparation for laser cutting
- Scale
- Contours
- RemaptoCplane/ProjecttoCplane
- Text object for Numbering
- (See link above for quick numbering using Grasshopper)
- Export Selected

```

# Practice Assignment

Generate a closed object using any of the methods we've explored (i.e. lofting/sweeping and creating a solid, revolving a profile curve, primitive volumes and boolean operations, etc.).  "Sculpt" the object using CageEdit.  Scale your object so that it fits within a 8"x8"x8" box.  Create numbered contours of your object assuming a material thickness of 3/16" and arrange these contours within the bounds of up to two 18"x24" rectangles (which represent the material sheets).  Add two new layers to your model, one called 'Cut' and set to color Blue, and one called 'Engrave' set to color Red.  Add your contour curves to layer 'Cut' and your numbers to layer 'Engrave.'  If you use the Grasshopper file to generate and Bake the numbers of your contours, make sure to Explode the numbers in order to get the outline curves of the text objects.  Upload the numbered contour curves arranged on the material sheets to the link above.  Include your name in the filename.
