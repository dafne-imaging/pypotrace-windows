# pypotrace-windows
Building pypotrace for MSVC

This is a clone of repository https://github.com/flupke/pypotrace

With some adaptations to be compiled under Windows/MSVC

First, build the potrace library (or use the distributed binary in this repo) with MinGW. Make sure of running ``./configure --with-libpotrace``
Copy the dll and the lib files to the base of this repo. (If a lib file is not generated, see https://stackoverflow.com/questions/9360280/how-to-make-a-lib-file-when-have-a-dll-file-and-a-header-file)

Then build the agg_mini library (it's just the small part of the AGG library that the extension actually uses):
``cl /c /MD agg_curves.cpp``

Copy the agg_curves.obj file into the base directory.

Finally, run the python setup:
``python setup.py build_ext -I"C:/Python38/Lib/site-packages/numpy/core/include;C:/src/potrace-1.16/src;agg_mini" --inplace``
Replace the path ``C:/src/potrace-1.16/src`` with the location of the potrace source.