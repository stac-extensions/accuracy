# Accuracy Extension Specification

- **Title:** Accuracy
- **Identifier:** <https://stac-extensions.github.io/accuracy/v1.0.0/schema.json>
- **Field Name Prefix:** accuracy
- **Scope:** Item, Collection
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @matthewhanson

This document explains the Accuracy Extension to the
[SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) 
specification. Included are fields to provide estimates of accuracy, both geometric
and measurement (e.g., radiometric) accuracy.

- Examples:
  - [Item example](examples/item.json): Shows the basic usage of the extension in a STAC Item
  - [Collection example](examples/collection.json): Shows the basic usage of the extension in a STAC Collection
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## Item Properties and Collection Fields

| Field Name                    | Type   | Description |
| ----------------------------- | ------ | ----------- |
| accuracy:geometric_x_bias     | number | An estimate of the geometric bias in the x direction. |
| accuracy:geometric_y_bias     | number | An estimate of the geometric bias in the y direction. |
| accuracy:geometric_x_stddev   | number | An estimate of the geometric standard deviation in the x direction. |
| accuracy:geometric_y_stddev   | number | An estimate of the geometric standard deviation in the y direction. |
| accuracy:geometric_rmse       | number | Radial root mean square error (rRMSE), in meters. |
| accuracy:measurement_relative | number | The measurement relative uncertainty, in the measured units. |
| accuracy:measurement_absolute | number | The measurement absolute uncertainty, in the measured units. |

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
