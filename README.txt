The colors on this square can only be red or green, not blue. 
I did this on purpose to give a bonus challenge. 

If students are interested in experimenting, they can try to add 
a blue color. This requires a change in the pipelineCreateInfo,
a change in the vertex structure, a change in the shaders,
and a change in the SquareDataArrays file. This extra challenge
is completely optional though. Future tutorials do NOT depend
on the ability to draw full RGB color via the method in this tutorial.
What is mandatory, is understanding how basic Red-Green colors work,
because textures will build off of this tutorial in the future.

To go from a black square, to a square with some color, there
are several steps we need to take. In the Square.vert vertex
shader, we need the ability to take color as input from the 
vertex buffer (color will be in the vertex buffer, that is 
explained later), then we need to export color from the vertices
to the rasterizer, so that color is interpolated accross all 
pixels, and made available in the fragment shader (Square.frag).
Color goes from the vertex shader, to the rasterizer, to the
fragment shader. Then, in the fragment shader, we export the color
that we got from the rasterizer

We add a new array in the SquareDataArrays file
to hold colors. This holds the red and green value for each vertex.
If you want full RGB, add a blue value for every vertex.

Inside VertexStructure, we add an array of two floats for color,
this can be turned into three floats if you want full RGB
In Prepare_vb_ib(), we have to include the color of each vertex
into the vertex buffer.
In prepare_pipeline, we have to setup the VkVertexInputBindingDescription
with an array of VkVertexInputAttributeDescription. Previously, there
was only one attribute for position, and the position had a format
of R32-G32-B32, for three floats. Color will have two floats, so it
will have the format R32-G32. If you want a blue channel, make it three
floats. If you want four floats for alpha transparency, R32-G32-B32-A32

