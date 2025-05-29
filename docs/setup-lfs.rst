Setup LFS
=========


Caches regression data repositories and atom data files. Fails if cache is not available. Please use the `lfs-cache` reusable workflow to create the cache if not available.


Inputs
------

``regression-data-repo``
^^^^^^^^^^^^^^^^^^^^^^^^
* **Description:** Repository containing regression data (format: owner/repo)
* **Required:** No
* **Default:** ``tardis-sn/tardis-regression-data``

``atom-data-sparse``
^^^^^^^^^^^^^^^^^^^^
* **Description:** If true, only downloads atom_data/kurucz_cd23_chianti_H_He.h5 instead of full regression data
* **Required:** No
* **Default:** ``false``

Usage
-----

.. code-block:: yaml

   - name: Setup Git LFS
     uses: tardis-sn/tardis-actions/setup-lfs@main
     with:
       regression-data-repo: tardis-sn/tardis-regression-data
       atom-data-sparse: true

What it does
------------

1. **Clones Repository:** Checks out the specified regression data repository
2. **Creates LFS File List:** Generates a list of LFS files (full or sparse based on input)
3. **Restores LFS Cache:** Attempts to restore cached LFS objects and fails if cache is missing

Cache Behavior
--------------

This action **requires** an existing LFS cache and will fail if no cache is found. This is to prevent accidental git pulls. The cache key is generated based on:

* Repository name (e.g. ``tardis-regression``)
* Checkout mode (``atom-data-sparse`` or ``full-data``)
* Hash of LFS file list
* Repository identifier (e.g. ``owner/repo``)
* Cache version (e.g. ``v1``)

