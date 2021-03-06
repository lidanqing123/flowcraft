mash_dist
=========

Purpose
-------

This component executes mash dist to find plasmids
within high throughoput sequencing data, using as inputs fasta files
(e.g. contigs). Then, the resulting file can
be imported into `pATLAS <http://www.patlas.site/>`_.
This component calculates pairwise distances between sequences
(one from the database and the query sequence).
However, this process can be user for other purposes, by providing a different
database than the default that is intended for plasmid searches.

.. note::
    - pATLAs documentation can be found `here <https://tiagofilipe12.gitbooks.io/patlas/content/>`_.
    - MASH documentation can be found `here <https://mash.readthedocs.io/en/latest/>`_.


Input/Output type
------------------

- Input type: ``fasta``
- Output type: ``json``


Parameters
----------

- ``mash_distance``: Sets the maximum distance between two sequences to be
  included in the output. Default: 0.1.

.. note::
    The subtraction of 1 - `mash_distance` can be used as an approximation to
    Average Nucleotide Identity (ANI). For instance a mash distance of 0.1 well
    correlates with ANI at 0.9 (90%).

- ``pValue``: P-value cutoff for the distance estimation between two sequences
  to be included in the output. Default: 0.05.

- ``shared_hashes``: Sets a minimum percentage of hashes shared between two
  sequences in order to include its result in the output. Default: 0.8.

- ``refFile``: Specifies the reference file to be provided to mash. It can either
  be a fasta or a .msh reference sketch generated by mash.
  Default: '/ngstools/data/patlas.msh'. If the component ``mash_sketch_fasta``
  is executed before this component, this parameter will be ignored and instead
  the secondary link between the two processes will be used to feed this
  component with the reference sketch.


Published results
-----------------

- ``results/mashdist/``: A `JSON` file that can be imported to `pATLAS <http://www.patlas.site/>`_
  with the results from mash dist.


Published reports
-----------------

None.


Default directives
------------------

- ``runMashDist``:
    - ``container``: flowcraft/mash-patlas
    - ``version``: 1.6.0-1
- ``mashDistOutputJson``:
    - ``container``: flowcraft/mash-patlas
    - ``version``: 1.6.0-1
