.. only:: html

    .. note::
        :class: sphx-glr-download-link-note

        Click :ref:`here <sphx_glr_download_auto_examples_plotting_plot_qc.py>`     to download the full example code
    .. rst-class:: sphx-glr-example-title

    .. _sphx_glr_auto_examples_plotting_plot_qc.py:


quality control plots
=====================

This example shows you the inbuilt quality control plots from besca.


.. code-block:: default


    #import libraries
    import besca as bc
    import matplotlib.pyplot as plt








Before beginning any analysis it is useful to take a detailled look at your dataset
to get an understanding for its characteristics.


.. code-block:: default


    #import data
    adata = bc.datasets.pbmc3k_raw()








transcript capture efficiency
-----------------------------

Plotting the transcript capture efficiency will give you an overview of the expression
of genes within cells relative to the total UMI counts.


.. code-block:: default


    #transcript capture efficiency
    fig, ax = plt.subplots(1)
    fig.set_figwidth(8)
    fig.set_figheight(5)
    fig.tight_layout()

    bc.pl.transcript_capture_efficiency(adata,ax=ax)




.. image:: /auto_examples/plotting/images/sphx_glr_plot_qc_001.png
    :alt: transcript capture efficiency
    :class: sphx-glr-single-img





overview of library size unprocessed
------------------------------------

This gives you an overview of the read distribution per cell. High quality cells
will have a larger number of reads per cell and this is a parameter you can use to 
filter out low quality cells. The number of reads you would expect per cell is strongly
dependent on the single-cell sequencing method you used.


.. code-block:: default


    bc.pl.librarysize_overview(adata)




.. image:: /auto_examples/plotting/images/sphx_glr_plot_qc_002.png
    :alt: library size distribution, NODG, dropouts
    :class: sphx-glr-single-img


.. rst-class:: sphx-glr-script-out

 Out:

 .. code-block:: none

    /pstore/home/julienla/.conda/envs/besca_docs/lib/python3.7/site-packages/seaborn/distributions.py:2551: FutureWarning:

    `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).

    /pstore/home/julienla/.conda/envs/besca_docs/lib/python3.7/site-packages/seaborn/distributions.py:2551: FutureWarning:

    `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).


    <Figure size 1100x800 with 3 Axes>



most strongly expressed transcripts
-----------------------------------

This will let you identify the genes which dominant your experiment 
(generally you would expect mitochondrial and ribosomal genes, 
in this dataset these genes have been removed beforehand).


.. code-block:: default


    bc.pl.top_genes_counts(adata=adata, top_n=25)




.. image:: /auto_examples/plotting/images/sphx_glr_plot_qc_003.png
    :alt: Top 25 genes account for 25.24% of all UMI counts
    :class: sphx-glr-single-img


.. rst-class:: sphx-glr-script-out

 Out:

 .. code-block:: none


    <AxesSubplot:title={'center':'Top 25 genes account for 25.24% of all UMI counts'}, xlabel='fraction of UMI counts per cell', ylabel='gene'>



visualize the processed dataset
-------------------------------

After performing your filtering it is generally a good idea to take another look
at your dataset to ensure that the filtering parameters used were reasonable.


.. code-block:: default


    adata = bc.datasets.pbmc3k_processed()








Please note that the displayed counts have already been scaled. You would now expect
a more or less normal distribution of library size within your dataset.


.. code-block:: default


    bc.pl.librarysize_overview(adata)



.. image:: /auto_examples/plotting/images/sphx_glr_plot_qc_004.png
    :alt: library size distribution, NODG, dropouts
    :class: sphx-glr-single-img


.. rst-class:: sphx-glr-script-out

 Out:

 .. code-block:: none

    /pstore/home/julienla/.conda/envs/besca_docs/lib/python3.7/site-packages/seaborn/distributions.py:2551: FutureWarning:

    `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).

    /pstore/home/julienla/.conda/envs/besca_docs/lib/python3.7/site-packages/seaborn/distributions.py:305: UserWarning:

    Dataset has 0 variance; skipping density estimate.

    /pstore/home/julienla/.conda/envs/besca_docs/lib/python3.7/site-packages/seaborn/distributions.py:2551: FutureWarning:

    `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).


    <Figure size 1100x800 with 3 Axes>




.. rst-class:: sphx-glr-timing

   **Total running time of the script:** ( 0 minutes  7.755 seconds)


.. _sphx_glr_download_auto_examples_plotting_plot_qc.py:


.. only :: html

 .. container:: sphx-glr-footer
    :class: sphx-glr-footer-example



  .. container:: sphx-glr-download sphx-glr-download-python

     :download:`Download Python source code: plot_qc.py <plot_qc.py>`



  .. container:: sphx-glr-download sphx-glr-download-jupyter

     :download:`Download Jupyter notebook: plot_qc.ipynb <plot_qc.ipynb>`


.. only:: html

 .. rst-class:: sphx-glr-signature

    `Gallery generated by Sphinx-Gallery <https://sphinx-gallery.github.io>`_
