

.. _sphx_glr_auto_examples_plot_procrustes.py:


=============================
Aligning two matrices with the procrustes function
=============================

In this example, we load in some synthetic data, rotate it, and then use the
procustes function to get the datasets back in alignment.  The procrustes
function uses linear transformations to project a source matrix into the
space of a target matrix.




.. rst-class:: sphx-glr-horizontal


    *

      .. image:: /auto_examples/images/sphx_glr_plot_procrustes_001.png
            :scale: 47

    *

      .. image:: /auto_examples/images/sphx_glr_plot_procrustes_002.png
            :scale: 47





.. code-block:: python


    # Code source: Andrew Heusser
    # License: MIT

    import hypertools as hyp
    import scipy.io as sio
    import numpy as np
    import matplotlib.pyplot as plt

    data = hyp.tools.load('spiral')
    target = data

    # A random rotation matrix
    rot = np.array([[-0.89433495, -0.44719485, -0.01348182],
           [-0.43426149,  0.87492975, -0.21427761],
           [-0.10761949,  0.18578133,  0.97667976]])
    # creating new spiral with some noise
    source = np.dot(target, rot)

    # Before hyperalignment
    fig,ax,data = hyp.plot([target, source], show=False, return_data=True)
    ax.set_title('Before Procrustes')
    plt.show()

    # After hyperalignment
    fig,ax,data = hyp.plot([hyp.tools.procrustes(source, target), target], ['-','--'], show=False, return_data=True)
    ax.set_title('After Procrustes')
    plt.show()

**Total running time of the script:** ( 0 minutes  0.563 seconds)



.. container:: sphx-glr-footer


  .. container:: sphx-glr-download

     :download:`Download Python source code: plot_procrustes.py <plot_procrustes.py>`



  .. container:: sphx-glr-download

     :download:`Download Jupyter notebook: plot_procrustes.ipynb <plot_procrustes.ipynb>`

.. rst-class:: sphx-glr-signature

    `Generated by Sphinx-Gallery <http://sphinx-gallery.readthedocs.io>`_
