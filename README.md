# TriangleGeometry
I noticed [Three JS primitives](https://threejs.org/manual/#en/primitives) excludes triangular planes. After an [unsuccessful PR](https://github.com/mrdoob/three.js/pull/29882) to remedy the issue, I decided to post the code here, should anyone else find it useful. This generator has the following params: **width**, **height**, **skew**, and **segments**.

While the default parameters create an _equilateral_ triangle, adjusting the width / height / skew will produce any type (isosceles, scalene, right, obtuse). Segments are the number of edges on a given side, used for uniform subdivision. Here is a 16 segment example:

![image](https://github.com/user-attachments/assets/fbde3e93-1b25-4ba8-a8bb-28de446f035f)

# Use
Add the code to your project and import as you would any other module:

`import { TriangleGeometry } from '<path-to-file>/TriangleGeometry.js';`

Instantiate like any other class:
```
const equilateral = new TriangleGeometry();
const isosceles   = new TriangleGeometry( 1, 1 );
const scalene     = new TriangleGeometry( 1, 1, 0.5 );
const right       = new TriangleGeometry( 1, 1, 1 );
const obtuse      = new TriangleGeometry( 1, 1, 2 );
const threeJsLogo = new TriangleGeometry( 1, Math.sqrt( 3 ) / 2, 0, 4 );
```

# Purpose
Skipping over the tedium of [creating geometry manually](https://threejs.org/docs/index.html?q=geom#api/en/core/BufferGeometry), and unless you want [a triangle with exactly 4 vertices](https://threejs.org/docs/index.html?q=circle#api/en/geometries/CircleGeometry), there is no clean way to create simple or subdivided triangles in Three JS.

Simple triangles are useful in any planar example where 1 less vertex allows 25% more stuff. Subdivided triangles are useful when vertex transformations are needed. These kinds of effeciency are notable at scale, as is the case with procedural applications (ie. landscapes, grass, particles, billboards, softbodies, etc.).
