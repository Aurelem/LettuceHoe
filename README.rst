==========
LettuceHoe 
==========

Python package to run segmentation on the workspace defined on an image of crops and computes a modified boustrophedon path for the tool to hoe around cultivated plants. 

------------
Dependencies
------------

numpy and the python binding to OpenCV. For Debian/Ubuntu:

.. code:: bash

    apt-get install python-numpy python-opencv


-------
Install
-------

In the source folder, run:

.. code:: bash

    python setup.py install

-------
Example
-------

.. code:: python

  import lettucehoe as lh

  fname="data/pics/OH.jpg"
  im=lh.cv2.imread(fname)

  #Workspace parameters [x0, y0, dx, dy]
  ws_par=[970, 140, 700,500]
  tool_size=50

  omask=lh.plantmask(im, ws_par, tool_size)
  toolPath=lh.mod_boustrophedon(omask, im, tool_size, ws_par)
  lh.np.savetxt("data/toolPath.txt", toolPath)

.. image:: data/pics/example.png
