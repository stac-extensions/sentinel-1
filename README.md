# Sentinel-1 Extension Specification

- **Title:** Sentinel-1
- **Identifier:** <https://stac-extensions.github.io/sentinel-1/v1.0.0/schema.json>
- **Field Name Prefix:** s1
- **Scope:** Item, Collection
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @m-mohr

This document explains the Sentinel-1 Extension to the [SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification.

The intention of the first version of the specification is to define the existing behavior of
the properties prefixed with `s1` as created by the [stactools-sentinel1](https://github.com/stactools-packages/sentinel1)
package and used by [Earth Search](https://earth-search.aws.element84.com/v1) and
[Microsoft Planetary Computer](https://planetarycomputer.microsoft.com/api/stac/v1). Future versions
will aspire to standardize fields such as the numerous coverage calculations into separate extensions
that are not specific to Sentinel-1.

- Examples:
  - [Item example](examples/item.json): Shows the basic usage of the extension in a STAC Item (todo)
  - [Collection example](examples/collection.json): Shows the basic usage of the extension in a STAC Collection (todo)
- [JSON Schema](json-schema/schema.json) (todo)
- [Changelog](./CHANGELOG.md) (todo)

## Fields

The fields in the table below can be used in these parts of STAC documents:

- [ ] Catalogs
- [ ] Collections
- [x] Item Properties (incl. Summaries in Collections)
- [ ] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections)
- [ ] Links

| Field Name                     | Type      | Description                                                  | From             |
| ------------------------------ | --------- | ------------------------------------------------------------ | ---------------- |
| s1:datatake_id                 | string    | e.g. `420895`                                                | Earth Search L1C |
| s1:instrument_configuration_ID | string    | e.g. `7`                                                     | Earth Search L1C |
| s1:orbit_source                | string    | e.g. `PREORB`                                                | Earth Search L1C |
| s1:processing_datetime         | string    | RFC3339 datetime in UTC                                      | Earth Search L1C |
| s1:processing_level            | string    | e.g. `1`                                                     | Earth Search L1C |
| s1:product_identifier          | string    | e.g. `S1A_IW_GRDH_1SDV_20240318T153023_20240318T153035_053038_066C1F_F913` | Earth Search L1C |
| s1:product_timeliness          | string    | e.g. `NRT-3h`                                                | Earth Search L1C |
| s1:resolution                  | string    | e.g. `high`                                                  | Earth Search L1C |
| s1:slice_number                | string    | e.g. `17`                                                    | Earth Search L1C |
| s1:total_slices                | string    | e.g. `17`                                                    | Earth Search L1C |
| s1:shape                       | [integer] | **DEPRECATED** Use proj:shape instead                        | Earth Search L1C |

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
