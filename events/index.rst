Events
######

This page provides event-specific documentation for short-term events such as hackathons.


UK National GPU Hackathon 2022
==============================


The `UK National GPU Hackathon 2022 <https://www.gpuhackathons.org/event/uk-national-gpu-hackathon-2022>`__ is an event for scientists to accelerate their AI or HPC research codes under the guidance of expert GPU mentors from National Labs, Universities and industry leaders in a collaborative environment.

For the 2022 UK National GPU Hackathon, Bede is serving as one of the Tier 2 HPC systems available to teams participating in the event. 


This involves hardware reservations of:

* A 2 node (8 GPU) reservation shared between participating teams from ``2022-02-28`` ``09:00:00`` to ``2022-03-01`` ``09:00:00``
* A single node (4 GPU) reservation per team (5 nodes total) from ``2022-03-04`` to ``2022-03-10`` ``09:00:00``

  * Nodes will become available for use after an OS upgrade on the ``2022-03-04``

During this time, these nodes will not be available for general Bede usage.

Teams will have been assigned slurm account(s) via email, which will provide access to the node reservations during the above time periods.

.. note:: 

  As this event is taking place during Bede's :ref:`migration to RHEL 8 <RHEL8-migration>`, hackathon participants will have to take some additional steps when using bede.

  The reserved nodes will be using the RHEL 8 image, to provide access to CUDA 11 which is not available under RHEL 7, however, on connection to bede users will be entered into a RHEL 7 session, and must execute the ``login8`` command to switch on to the interactive RHEL 8 image.


Connecting to Bede
------------------

Bede is accessed via SSH, which at the time of the event will connect users to a RHEL 7 environment.

.. code-block:: console

   ssh USERNAME@login1.bede.dur.ac.uk


Hackathon participants must switch to the RHEL 8 environment in order to make use of the hardware reservations, which are running on RHEL 8 images which provide access to recent CUDA and NVHPC versions.

.. code-block:: console

    login8

Building your code
------------------

On Bede, the login nodes are the only form of interactive session available.
Login nodes do not have exclusive resource allocation, so please be considerate of other users when using these nodes. 

I.e. limit the number of CPU cores and memory used during compilation to avoid negatively impacting the experience of other users.

Currently, the RHEL 8 login node also contains 4 NVIDIA T4 GPUs, which may be used to for short testing of applications prior to batch job submission. 
However, as these resources are shared you may wish to use ``CUDA_VISIBLE_DEVICES``  to avoid all users executing on Device 0.

Alternatively, you can submit batch jobs which will compiler your applications with limited resources.

Submitting Batch Jobs
---------------------

During the hackathon, you may submit batch jobs to the hardware reserved node(s) using the assigned slurm account (of the form ``bddirXX``, where ``XX`` is between ``07`` and ``11`` inclusive.)

When using Bede, Slurm is configured to provide CPUs and memory in line with the fraction of GPUs within a node requested. 

I.e. requesting 1 of 4 GPUs in a node will provide 1/4 of the CPUs and 1/4 of the RAM of the node.

.. code-block:: slurm

   #!/bin/bash

   # Generic options:

   #SBATCH --account=bddirXX  # Run job under project bddirXX
   #SBATCH --time=01:00:00    # Run for a max of 1 hour

   # Node resources:

   #SBATCH --partition=gpu    # use the gpu partition for the V100 nodes reserved for the hackathon
   #SBATCH --nodes=1          # Resources from a single node
   #SBATCH --gres=gpu:1       # one GPU per node (plus 25% of node CPU and RAM per node)

   # Run commands:

   module load cuda
   nvcc --version

This can then be submit via ``sbatch``. 

I.e. if the above job submission script is named ``myjob.sh`` in the current working directory:

.. code-block:: console

    sbatch myjob.sh

.. note:: 

    You **must** submit your jobs from a RHEL 8 session to make use of the hackathon reservation.

Job progress can be checked via slurm commands such as ``squeue`` and ``sacct`` 

.. code-block:: bash

    # List jobs for the current user
    squeue -u $USER
    # List jobs for a given account
    squeue -A bddirXX
    # List jobs for a given reservation
    squeue -R bddirXX_YY
    # View accounting information for a completed job
    sacct -j <JOB_ID>

More Information
----------------

Please refer to the :ref:`Using Bede<using-bede>`, :ref:`Hardware<hardware>` and :ref:`Software<software>` sections of this documentation for non-hackathon specific information, or ask questions on the `#support-bede<https://ukhackathon2022.slack.com/app_redirect?channel=support-bede>` channel in the `event slack workspace <ukhackathon2022.slack.com>`__.

