.. _software-libraries-MPI:

MPI
===

`OpenMPI <https://www.open-mpi.org/>`__ and `MVAPICH <https://mvapich.cse.ohio-state.edu/>`__ are provided as alternate Message Passing Interface (MPI) implementations on Bede.

OpenMPI is the main supported MPI on bede.

We commit to the following convention for all MPIs we provide as modules:

- The wrapper to compile C programs is called ``mpicc``
- The wrapper to compile C++ programs is called ``mpicxx``
- The wrapper to compile Fortran programs is called ``mpif90``

CUDA-enabled MPI is available through OpenMPI, when a cuda module is loaded alongside ``openmpi``, I.e.

.. code-block:: bash

   module load gcc cuda openmpi

OpenMPI is provided by the ``openmpi`` module(s):

.. code-block:: bash

   module load openmpi
   module load openmpi/4.0.5


MVAPICH2 is provided by the `mvapich2` module(s):

.. code-block:: bash

   module load mvapich2
   module load mvapich2/2.3.5
   module load mvapich2/2.3.5-2


.. note::

   The ``mvapich2/2.3.5-2`` module should be used rather than ``mvapich2/2.3.5``, which is only provided to support existing projects which depend on it.

   Under RHEL 8, the ``mvapich2/2.3.5`` module is removed.