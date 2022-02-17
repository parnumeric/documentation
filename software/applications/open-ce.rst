.. _software-applications-open-ce:

Open-CE
=======

The `Open Cognitive Environment (Open-CE) <https://osuosl.org/services/powerdev/opence/>`__ is a community driven software distribution for machine learning and deep learning frameworks.

Open-CE software is distributed via :ref:`Conda<software-applications-conda>`, with all included packages for a given Open-CE release being installable in to the same conda environment.

Open-CE conda channels suitable for use on Bede's IBM Power architecture systems are hosted by `Oregon State University <https://osuosl.org/services/powerdev/opence/>`__ and `MIT <https://opence.mit.edu/>`__.

It is the successor to :ref:`IBM WMLCE <software-applications-wmlce>` which was archived on 2020-11-10 with IBM WMLCE 1.7.0 being the final release.

.. note:: 

   Open-CE does not include all features from WMLCE, such as TensorFlow Large Model Support. 


Open-CE includes the following software packages, amongst others:

* :ref:`TensorFlow <software-applications-tensorflow>`
* :ref:`PyTorch <software-applications-pytorch>`
* `Horovod <https://horovod.ai/>`__
* `ONNX <https://onnx.ai/>`__


Using Open-CE
-------------

Open-CE provides software packages via :ref:`Conda<software-applications-conda>`, which you must first :ref:`install<software-applications-conda-installing>`.

With a working conda install, Open-CE packages can be installed from either the OSU or MIT conda channels.


I.e. to install ``tensorflow`` and ``pytorch`` from OSU Open-CE conda channel

.. code-block:: bash

   # Create a new conda environment named open-ce, if necessary
   conda create -y --name open-ce python==3.9

   # Activate the conda environment
   conda activate open-ce

   # Install the required conda package, specifying the channel to install from
   conda install -c https://ftp.osuosl.org/pub/open-ce/current/ tensorflow
   conda install -c https://ftp.osuosl.org/pub/open-ce/current/ pytorch

Once installed into a conda environment, the Open-CE provided software packages can be used interactivly on login nodes or within batch jobs by activating the named conda environment.

.. code-block:: bash

   # activate the conda environment
   conda activate open-ce

   # Run a python command or script which makes use of the installed packages
   # I.e. to output the version of tensorflow:
   python3 -c "import tensorflow;print(tensorflow.__version)"

    # I.e. or to output the version of pytorch:
   python3 -c "import torch;print(torch.__version)"

Why use Open-CE
---------------

@todo - explain why you might want to use them compared to just conda installs of tf/torch?


Differences from WMLCE
----------------------

@todo - emphasise the differences between wmlce in a subsection?
No LMS. 
No ddlrun? 


Benchmark
---------

@todo - benchmarks


todo
----

https://openpowerfoundation.org/blog/open-cognitive-environment-open-ce-a-valuable-tool-for-ai-researchers/



