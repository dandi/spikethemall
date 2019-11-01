# SpikoDrome

**Note**: name might still change [see #3](https://github.com/spikodrome/administrative/issues/3)

SpikoDrome is a concerted effort across multiple projects: [DANDI](https://github.com/dandi), [SpikeForest](https://spikeforest.flatironinstitute.org), [SpikeInterface](https://github.com/SpikeInterface).

This repository is merely a high-level administrative area for orchestrating the project.

## High level description of the subprojects

We want to provide

- [Datasets](https://github.com/spikodrome/datasets) - a
  collection of datasets with raw + curated spike sorted data, in NWB format, with nice provenance attached.
  - Datasets will be used by SpikeForest for "live" benchmarking of available spike sorters
- [App](https://github.com/spikodrome/administrative/issues/4) -
  a turnkey app based on https://github.com/SpikeInterface/ and https://github.com/flatironinstitute/spikeforest/
  to make it easy for ppl to run a collection of spike sorters, with nice reports, and eventually interface to curate them
  - that app will be available on dandiarchive but also available locally
  - people would be able to submit their curated data for their or someone's data
  - app will allow for submission of results (no actual raw or curated data) users obtain locally
- **MetaSort** -
  - eventually the app would embed and use knowledge on optimal sorting strategy for a given type of data (electrodes/species/cell_type)
  
## Goals

- Provide empirical guidance for the choice of spike sorting algorithm and curation methods
- Investigate the degree of lab-specific idiosyncracies in spike sorting
- Provide a nice demonstration for benefits of using standard rich (NWB) file format
- Establish collection of provenance information for spike sorted data
