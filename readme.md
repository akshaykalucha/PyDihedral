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

```python
from pydihedral import Dihedral

## set of all symmetry transformation of an equilateral triangle.
d3 = Dihedral(3)

# List the vertices in the group
d3.vertices()
# [0, 1, 2]

# Perform a rotation of 240 degrees on the vertices
d3.apply(d3.r[2])
# [2, 0, 1]

# Rotate vertex 0 by 120 degrees
d3.apply(d3.r[1], [0])
# [1]
```

## Composing symmetries
Symmetries can be combined using the `compose` method.

```python
# Compose a rotation with reflection (f_2(r_1))
composed_symmetry = d3.compose([d3.f[2], d3.r[1]])

# Apply the symmetry to vertex 1
d3.apply(composed_symmetry, [1])
# [2]
```

## Finding subgroups
There is a general classification of all subgroups of 𝐷𝑛 for every 𝑛.

```Theorem: Every subgroup of 𝐷𝑛=⟨𝑟,𝑠⟩ is is either cyclic or dihedral, and a complete listing of the subgroups is as follows:

(1) ⟨𝑟𝑑⟩, where 𝑑∣𝑛, with index 2𝑑,

(2) ⟨𝑟𝑑,𝑟𝑖𝑠⟩, where 𝑑∣𝑛, 0≤𝑖≤𝑑−1, with index 𝑑.
```

Every subgroup of 𝐷𝑛 occurs exactly once in this listing.
The method `subgroups` returns all subgroups in the dihedral group by generating all possible subsets of the group and
verifying relevant group properties (identity, closure).

```python
d3.subgroups()
# [['r0'], ['r0', 'f0'], ['r0', 'f1'], ['r0', 'f2'], ['r0', 'r1', 'r2'], ['r0', 'r1', 'r2', 'f0', 'f1', 'f2']]
```

Specific subsets can also be verified as being a subgroup or not using the `has_subgroup` method. This method takes a list of actions or another `D` instance.

```python
d6 = D(6)
d3 = D(3)

d6.has_subgroup(d3)
# True

d6.has_subgroup([d6.r[0], d6.r[1]])
# False

d6.has_subgroup([d6.r[0]])
# True
```

# Reducing operations

While `compose` combines operations, they can be reduced to a readable format using `reduce_operations`. For example,

```python
# Reduce r_1(s_2)
d3.reduce_operations(([d3.r[1], d3.f[2]]))
# s0
```