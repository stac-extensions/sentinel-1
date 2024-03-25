# Sentinel-1 Extension Specification

- **Title:** Sentinel-1
- **Identifier:** <https://stac-extensions.github.io/sentinel-1/v0.1.0/schema.json>
- **Field Name Prefix:** s1
- **Scope:** Item
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @m-mohr

This document explains the Sentinel-1 Extension to the
[SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification.

The intention of the first version of the specification is to define the existing behavior of
the properties prefixed with `s1` as created by the [stactools-sentinel1](https://github.com/stactools-packages/sentinel1)
package and used by [Earth Search](https://earth-search.aws.element84.com/v1) and
[Microsoft Planetary Computer](https://planetarycomputer.microsoft.com/api/stac/v1). Future versions
will aspire to standardize fields such as the numerous coverage calculations into separate extensions
that are not specific to Sentinel-1.

- Examples:
  - [Item: Microsoft Planetary Computer, Sentinel-1 GRD](examples/mspc-s1-grd.json)
  - [Item: Microsoft Planetary Computer, Sentinel-1 RTC](examples/mspc-s1-rtc.json)
  - [Item: Earth Search, Sentinel-1 GRD](examples/earthsearch-s1-grd.json)
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## Fields

The fields in the table below can be used in these parts of STAC documents:

- [ ] Catalogs
- [ ] Collections
- [x] Item Properties (incl. Summaries in Collections)
- [ ] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections)
- [ ] Links

| Field Name                     | Type      | Description                                                  |
| ------------------------------ | --------- | ------------------------------------------------------------ |
| s1:datatake_id                 | string    | e.g. `420895`                                                |
| s1:instrument_configuration_ID | string    | e.g. `7`                                                     |
| s1:orbit_source                | string    | e.g. `PREORB`                                                |
| s1:processing_datetime         | string    | RFC3339 datetime in UTC                                      |
| s1:product_identifier          | string    | e.g. `S1A_IW_GRDH_1SDV_20240318T153023_20240318T153035_053038_066C1F_F913` |
| s1:product_timeliness          | string    | e.g. `NRT-3h`, `Fast-24h`                                    |
| s1:resolution                  | string    | e.g. `high`                                                  |
| s1:slice_number                | string    | e.g. `17`                                                    |
| s1:total_slices                | string    | e.g. `17`                                                    |
| s1:processing_level            | string    | **DEPRECATED** Use processing:level instead                  |
| s1:shape                       | [integer] | **DEPRECATED** Use proj:shape instead                        |

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
