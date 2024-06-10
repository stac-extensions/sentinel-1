# Sentinel-1 Extension Specification

- **Title:** Sentinel-1
- **Identifier:** <https://stac-extensions.github.io/sentinel-1/v0.1.0/schema.json>
- **Field Name Prefix:** s1
- **Scope:** Item
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @m-mohr

This document explains the Sentinel-1 Extension to the
[SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification.

> \[!CAUTION]
> The intention of the first version of the specification was to reflect the existing behavior of the properties
> prefixed with `s1` as implemented by the [stactools-sentinel1](https://github.com/stactools-packages/sentinel1) package.
> The following version deprecated most of the fields in favor of other extensions that are not specific to Sentinel-1.
> The remaining fields are highly specific and usually not of interest of an average user.
> As such implementors should only implement the fields that they think bring value to their users.
> Many implementations may not need to implement this extension at all.

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
| s1:slice_number                | string    | e.g. `17`                                                    |
| s1:total_slices                | string    | e.g. `17`                                                    |
| s1:resolution                  | string    | **DEPRECATED** Expose `gsd`, `spatial_resolution` (raster extension), and/or `sar:resolution_range` `sar:resolution_azimuth` (SAR extension) instead. The mapping is available in Table B.1 of the [Sentinel-1 documentation](https://sentinel.esa.int/documents/247904/349449/s1_sp-1322_1.pdf). |
| s1:product_identifier          | string    | **DEPRECATED** Use Item `id` or link to source products instead (e.g. relation types `via` or `derived_from`) |
| s1:product_timeliness          | string    | **DEPRECATED** Use `product:timeliness_category` and `product:timeliness` instead |
| s1:processing_datetime         | string    | **DEPRECATED** Use `processing:datetime` instead             |
| s1:processing_level            | string    | **DEPRECATED** Use `processing:level` instead                |
| s1:shape                       | [integer] | **DEPRECATED** Use `proj:shape` instead                      |

**s1:resolution:** Either `full` (Full Resolution - SM mode), `high` (High Resolution - SM, IW and EW mode),
or `medium` (Medium Resolution - SM, IW, EW and WV modes)

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
