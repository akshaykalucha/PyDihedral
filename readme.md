# Py-Dihedral
While cyclic groups describe 2<em>D</em> objects that have only the rotational symmetry, the dihedral groups represents 2D objects that have rotational <em>and reflective</em> symmtery.
In general, a dihedral group is defined D<sub>n</sub> as a group of symmetries in a regular polygon of n-vertices. We think of this polygon as having vertices on the unit circle, these groups are most simple examples of any finite-group, and play major role in mathematics and physics.
with vertices labeled 0, 1, . . . , n−1 starting at (1, 0) and proceeding counterclockwise (A single <em>"Click"</em>)
at angles in multiples of 360/n degrees, that is, 2π/n radians. For example, D<sub>3</sub> represents the symmetries of a triangle.

### Project Description
Regular polygons have rotational and reflective symmetries. The dihedral group that describes the symmetry of a regular n-<em>gon</em>is written D𝑛.
In this code, a python class is implemented that outputs the structures of group of D<sub>n</sub> and also contains methods for generation (rotation and flip) and verification of subgroups and applying transformations as well.

### Symmetries of polygon
There are total of 2𝑛 different symmetries for a regular 𝑛-sided polygon.
Numbering vertices 1 through 𝑛, with 1 at the top. When you turn the arrangement into another arrangement, the vertices must be in the same order or the reverse order (a reflection), and the label at the top may be changed (a rotation). Therefore reflections and rotations are enough to give you all the possible symmetries of a polygon.

### Rotation Actions

<img src="https://upload.wikimedia.org/wikipedia/commons/b/b6/Dihedral4.png"/>

### Class Structure
An array `r[0], ..., r[n / 2]` stores the Rotation actions as class variable `r`, where the identity <em>`e`</em> rotation is r[0].
Reflections are stored in the same way in the class variable `f`, <em>flip</em>. Vertices are stores as numpy arrays in `v`, but can be accessed in a more readable integer format using the method `vertices`.


### Equilateral triangle case
D<sub>3</sub> is the symmetry group of an equilateral triangle, the dotted lines denote reflections, rotating the triangle from vetrex A to vertex B denotes a 120 degree turn
<img src="https://solitaryroad.com/c315/ole.gif"/>