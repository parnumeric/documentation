FAQ
=====

This page contains answers to the questions most frequently asked by Bede
users. 
The question list will be updated over time as more questions are
asked - if there is anything that you think should definitely be answered
here, please let us know by `Opening an Issue on GitHub <https://github.com/N8-CIR-Bede/documentation/issues/new>`__ or by contacting your `local Bede RSE <https://n8cir.org.uk/supporting-research/facilities/bede/rse-support-bede/>`__ .

How long can I run jobs for?
----------------------------

You can run jobs for a maximum of 48 hours, in either the ``gpu`` or ``infer``
partitions.
This is detailed in the :ref:`Usage section of the documentation<usage-maximum-job-runtime>`.

How can I acknowledge Bede in published or presented work?
----------------------------------------------------------------

You can acknowledge Bede using the standard text that we provide in :ref:`Acknowledging Bede<usage-acknowledging-bede>`:

.. include:: /common/acknowledging-bede.rst

How can I check my home directory quota?
----------------------------------------

You can use the following command:

.. code-block:: text

  quota -s

  Disk quotas for user XXXXXX (uid YYYYYYYY): 
       Filesystem   space   quota   limit   grace   files   quota   limit   grace
  nfs.bede.dur.ac.uk:/nfs/users
                   79544K      0K  20480M            1071       0       0

This tells me that, in this case, I have a limit of :code:`20480M`, and am 
currently using :code:`79544K` across 1071 files. 
For more information on using Bede's filesystems see the :ref:`File Storage <usage-file-storage>` documentation.

Where should I put project data?
--------------------------------

Project data that does not need to be backed up, e.g. intermediate results,
should be stored in the :code:`/nobackup/projects/<project>` directory, where
:code:`<project>` is your Bede project code.

Project data that should be backed up, e.g. final results that would be painful
to recompute, should be store in the :code:`/projects/<project>` directory.

.. note::
  Backups are **NOT** currently implemented on the :code:`/projects` filesystem!

How do I get started with Bede?
-------------------------------

The :ref:`Using Bede<using-bede>` page provides details on how to get registered, how to log in to the
machine and how to run jobs.

How can I add my own software?
------------------------------

It is recommended that you use :ref:`Spack<software-spack>` to extend the installed software on the system if possible.

Alternatively, the software you wish to use may provide instructions on local installation, or `contact your local Bede RSE <https://n8cir.org.uk/supporting-research/facilities/bede/rse-support-bede/>`__ for further guidance.

Is MATLAB available on Bede?
----------------------------

Unfortunately `MATLAB <https://www.mathworks.com/products/matlab.html>`__ is not available on Bede. MATLAB is not currently supported on IBM systems with a Power architecture.
It is possible to install `Octave <https://www.gnu.org/software/octave/index>`__ on Bede which can work as an alternative, although there is
currently no official support for this.


How can I suggest improvements or contribute to this documentation?
-------------------------------------------------------------------

The Bede documentation is maintained on GitHub at
`github.com/N8-CIR-Bede/documentation <https://github.com/N8-CIR-Bede/documentation>`__ where we welcome you to add issues
or to contribute by following the instructions in the README file. 


How can I get further help and support?
---------------------------------------
Each institution has Research Software Engineer support for Bede, and you can
find the support email address for your institution `on the N8CIR website
<https://n8cir.org.uk/supporting-research/facilities/bede/rse-support-bede/>`__.
There is also a `slack workspace <https://n8cirbede.slack.com>`__ that you can join to get further support and
contact the Bede user community. To request access, please e-mail: marion.weinzierl@durham.ac.uk.

