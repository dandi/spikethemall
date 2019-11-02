# Some notes on datalad usage

Much of this is posted from Yarik's comments on the issue tracker.

## Installing the spikodrome datasets super-dataset repo

```shell
$> datalad install https://github.com/spikodrome/datasets
[INFO   ] Cloning https://github.com/spikodrome/datasets [1 other candidates] into '/tmp/datasets' 
install(ok): /tmp/datasets (dataset)

$> cd datasets 
```

## Adding a dataset from an existing source

```
# if DataLad datasets already available somewhere  -- just install them in
$> datalad install -d . https://github.com/dandi-datasets/nwb_test_data
[INFO   ] Cloning https://github.com/dandi-datasets/nwb_test_data [1 other candidates] into '/tmp/datasets/nwb_test_data' 
[INFO   ]   Remote origin not usable by git-annex; setting annex-ignore                                                                                                                                                           
install(ok): nwb_test_data (dataset)
action summary:
  add (notneeded: 2, ok: 1)
  install (ok: 1)
  save (ok: 1)
```

Question: do we need to make a datalad save command here?

## Creating a new dataset
```
# create new:
$> datalad create -d . some-new-subdataset
[INFO   ] Creating a new annex repo at /tmp/datasets/some-new-subdataset 
create(ok): some-new-subdataset (dataset)
action summary:
  add (notneeded: 2, ok: 1)
  create (ok: 1)
  save (ok: 1)

$> cd some-new-subdataset
# and populate:
$> # here depends on either data is available online already or not - might use "datalad-crawler" extension, or "datalad addurls" command, or just "cp /somethings/* .; datalad save"   
$> # and then publish them independently somewhere. again would depend on if available or not
$> cd ..  # go to the top
$> datalad save -m "Added initial set of custom datasets"
```

## datalad-crawler

Questions: How does the datalad-crawler work? What if we have a custom way to retrieve data via python script? Can that be used for the crawler? Does the crawler relate to originally populating the dataset, or does it specify how git-annex retrieves the actual binaries?

## Publishing (or pushing back to the repo)

```
$> datalad publish  # to push back to this repo
```

Question: when working with datalad datasets, do we ever use git commands? (push, pull, commit, branch?)

## Structure of data

Notes from Yarik:

So, the ultimate workflow would depend on either we have those datasets already as datalad datasets, or they need to be created from scratch, and either data is already available online or not.

Then -- also .dat -> .nwb -- any such conversion should better be done via `datalad container-run` so we get a clear record and environment.

So may be within each subdataset we want some structure as well:

- `sourcedata/` -- in whatever format data was, if not .nwb to start with
- .... the rest to loosely follow something like [BIDS for neuroimaging](https://bids-specification.readthedocs.io). See examples among http://datasets.datalad.org/?dir=/openneuro . 
 We would need a separate issue for that discussion - so far we have only @bendichter 's summary from layouts of different labs: https://github.com/dandi/dandi-cli/issues/9  and haven't approached details.  But if we could stay closish to BIDS + [BIDS Common Derivatives](https://github.com/bids-standard/bids-specification/pull/265), at least in layout aspect -- would be great.
