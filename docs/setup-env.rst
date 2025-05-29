Setup Environment
=================

Sets up environment for TARDIS and caches it for faster subsequent builds.

This action downloads the conda-lock file, generates a cache key based on the file hash, and sets up a micromamba environment with caching capabilities.

Inputs
------

``os-label``
^^^^^^^^^^^^
* **Description:** OS label for lock file
* **Required:** Yes
* **Default:** ``linux-64``

``lock-file-url-prefix``
^^^^^^^^^^^^^^^^^^^^^^^^
* **Description:** URL for lock file
* **Required:** No
* **Default:** ``https://raw.githubusercontent.com/tardis-sn/tardis-base/master``

``environment-name``
^^^^^^^^^^^^^^^^^^^^
* **Description:** Name of the environment
* **Required:** No
* **Default:** ``tardis``

``cache-environment``
^^^^^^^^^^^^^^^^^^^^^
* **Description:** If true, cache the environment
* **Required:** No
* **Default:** ``true``

``cache-downloads``
^^^^^^^^^^^^^^^^^^^
* **Description:** If true, cache the downloads
* **Required:** No

Usage
-----

.. code-block:: yaml

   - name: Setup TARDIS Environment
     uses: tardis-sn/tardis-actions/setup-env@main
     with:
       os-label: osx-64
       lock-file-url-prefix: https://raw.githubusercontent.com/tardis-sn/tardis-base/master
       environment-name: tardis-environment
       cache-environment: false
       cache-downloads: true


What it does
------------

1. **Downloads Lock File:** Retrieves the conda lock file from the specified URL prefix
2. **Generates Cache Key:** Creates a unique hash-based cache key from the lock file contents
3. **Sets up Micromamba:** Uses the mamba-org/setup-micromamba action with caching enabled
4. **Caches Environment:** Optionally caches the conda environment and downloads for faster subsequent runs 
