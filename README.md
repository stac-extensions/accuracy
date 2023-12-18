# Accuracy Extension Specification

- **Title:** Accuracy
- **Identifier:** <https://stac-extensions.github.io/accuracy/v1.0.0-beta.1/schema.json>
- **Field Name Prefix:** accuracy
- **Scope:** Item, Collection
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @matthewhanson

This document explains the Accuracy Extension to the
[SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) 
specification. Included are fields to provide estimates of accuracy, both geometric
and measurement (e.g., radiometric) accuracy.

- Examples:
  - [Item example](examples/item.json): Example in Item Properties
  - [Bands in Item Assets example](examples/item-bands.json): Example in Bands in Item Assets (since STAC v1.1)
  - [Collection example](examples/collection.json): Example in a STAC Collection
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## Fields

The fields in the table below can be used in these parts of STAC documents:

- [ ] Catalogs
- [ ] Collections
- [x] Item Properties (incl. Summaries in Collections)
- [x] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections)
- [ ] Links
- [x] Bands

| Field Name                    | Type   | Description                                                         |
| ----------------------------- | ------ | ------------------------------------------------------------------- |
| accuracy:geometric_x_bias     | number | An estimate of the geometric bias in the x direction.               |
| accuracy:geometric_y_bias     | number | An estimate of the geometric bias in the y direction.               |
| accuracy:geometric_x_stddev   | number | An estimate of the geometric standard deviation in the x direction. |
| accuracy:geometric_y_stddev   | number | An estimate of the geometric standard deviation in the y direction. |
| accuracy:geometric_rmse       | number | Radial root mean square error (rRMSE), in meters.                   |
| accuracy:measurement_relative | number | The measurement relative uncertainty, in the measured units.        |
| accuracy:measurement_absolute | number | The measurement absolute uncertainty, in the measured units.        |

*At least one of the fields must be specified.*

## Relation types

The following types should be used as applicable `rel` types in the
[Link Object](https://github.com/radiantearth/stac-spec/tree/master/item-spec/item-spec.md#link-object).

| Type                 | Description                                                               |
| -------------------- | ------------------------------------------------------------------------- |
| radiometric-accuracy | URL describing the assessed absolute radiometric uncertainty of the data. |
| geometric-accuracy   | URL describing the assessed geometric accuracy of the data.               |

### Geometric Correction

Geometric corrections are steps that are taken to place the measurement accurately on the surface of the Earth
(that is, to geolocate the measurement) allowing measurements taken through time to be compared.

The focus of this extension is are the accuracy values, but the geometric correction directly influences the accuracy and as such
a number of additional relation types are provided here to guide users to information about the geometric correction.

| Type                 | Description                                        |
| -------------------- | -------------------------------------------------- |
| geometric-correction | URL to the Geometric Correction algorithm details. |
| elevation-model      | URL to the Digital Elevation Model (DEM).          |
| surface-model        | URL to the Digital Surface Model (DSM).            |

The relation types `elevation-model` and `surface-model` can be provided in any kind of file format (e.g., HTML or PDF),
but preferrably point to a STAC Collection or Item with additional metadata for the DEM/DSM.

## Contributing

All contributions are subject to the
[STAC Specification Code of Conduct](https://github.com/radiantearth/stac-spec/blob/master/CODE_OF_CONDUCT.md).
For contributions, please follow the
[STAC specification contributing guide](https://github.com/radiantearth/stac-spec/blob/master/CONTRIBUTING.md) Instructions
for running tests are copied here for convenience.

### Running tests

The same checks that run as checks on PR's are part of the repository and can be run locally to verify that changes are valid. 
To run tests locally, you'll need `npm`, which is a standard part of any [node.js installation](https://nodejs.org/en/download/).

First you'll need to install everything with npm once. Just navigate to the root of this repository and on 
your command line run:
```bash
npm install
```

Then to check markdown formatting and test the examples against the JSON schema, you can run:
```bash
npm test
```

This will spit out the same texts that you see online, and you can then go and fix your markdown or examples.

If the tests reveal formatting problems with the examples, you can fix them with:
```bash
npm run format-examples
```
