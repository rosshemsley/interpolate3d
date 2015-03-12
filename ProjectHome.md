## Note ##
This code is not actively maintained any more, and should be used with care (assume it is in 'beta' version)
It seems that the CGAL project now provides similar functionality, with much greater attention to details such as degeneracies and handling of large datasets.

http://doc.cgal.org/4.2/CGAL.CGAL.2D-and-Surface-Function-Interpolation/html/index.html#Chapter_2D_and_Surface_Function_Interpolation

However, if the dependency on CGAL is undesirable and your data is small (10s to 100s of thousands of points) and non-degenerate, this code may be worth considering.

## Purpose ##

Intended to give good interpolation results when input data is non-uniform, anisotropic and potentially sparse.

## Method ##

This code uses Natural Neighbour Interpolation. This requires that a Delaunay Mesh of the data is created, (a
simple flipping algorithm is used with robust predicates provided by (link to come). The Voronoi Cells are then
extracted, and the weighting function is computed based on the volumes stolen by the newly created Voronoi Cells.
I wrote a [short report](http://interpolate3d.googlecode.com/files/Report.pdf) explaining various interpolation functions and their implementations which this code was part of, this report can also be accessed from the download link.

## Creator ##

Created by [Ross Hemsley](http://www.cs.bris.ac.uk/home/rh7223/) for the Neutron Simulation package [Mcstas](http://www.mcstas.org/).

## Use ##

Code has been written not to require any external dependencies. Should simply compile and run. Read documentation in code for usage notes. **If you wish to use this code**, please drop me an e-mail to let me know what you are using it for.

## FAQ ##

**Q:** I can't seem to compile the code

**A:** The attached makefile will only work for the unit testing inside the main files, you will need to enable the testing by uncommenting the relevent lines in the file to use this.
If you wish to use example.c you need to compile it yourself, try

$ gcc example.c natural.c delauny.c utils.c -03