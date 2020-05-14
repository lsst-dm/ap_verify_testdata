`ap_verify_testdata`
====================

Data from `testdata_lsst` for small-scale tests of [`ap_verify`](https://github.com/lsst-dm/ap_verify/) functionality.

The data are identical to the files provided by [`testdata_lsst`](https://github.com/lsst/testdata_lsst/).
See that package for documentation of the file contents.

Relevant Files and Directories
------------------------------
path                  | description
:---------------------|:-----------------------------
`raw`                 | Raw fits files from [`testdata_lsst`](https://github.com/lsst/testdata_lsst/tree/master/data) in `i` band.
`calib`               | Master calibration files from `lsst-dev:/datasets/DC2/repoRun2.2i` for `i` band.
`config`              | Dataset-specific configs to help Stack code work with this dataset.
`templates`           | To be populated with `TemplateCoadd` images produced by a compatible version of the LSST pipelines. Must be organized as a filesystem-based Butler repo. Currently empty.
`repo`                | A template for a Butler raw data repository. This directory must never be written to; instead, it should be copied to a separate location, and data ingested into the copy (this is handled automatically by `ap_verify`, see below). Currently contains the appropriate `obs_lsst` `_mapper` file.
`refcats`             | A small Gaia reference catalog.
`dataIds.list`        | List of dataIds in this repo. For use in running Tasks. Currently set to run all Ids.


Git LFS
-------

To clone and use this repository, you'll need Git Large File Storage (LFS).

Our [Developer Guide](http://developer.lsst.io/en/latest/tools/git_lfs.html) explains how to setup Git LFS for LSST development.

Usage
-----

`ap_verify_testdata` is not included in `lsst_distrib` and is not available through `newinstall.sh`.
However, it can be installed explicitly with the [LSST Software Build Tool](https://developer.lsst.io/stack/lsstsw.html) or by cloning directly:

    git clone https://github.com/lsst/ap_verify_testdata/
    setup -r ap_verify_testdata

Unlike other datasets, `ap_verify_testdata` is not recognized by `ap_verify`'s normal command-line scripts.
It can be run through testing by calling `pytest` from the `ap_verify` installation directory, after `ap_verify` has been set up as normal.
