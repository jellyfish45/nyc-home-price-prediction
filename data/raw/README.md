# Raw sales data

Source: [NYC Department of Finance Rolling Sales Data](https://www.nyc.gov/site/finance/property/property-rolling-sales-data.page).

The five original borough workbooks cover October 1, 2025 through September 30, 2026. Their headers state that the sales data are as of October 8, 2026. Together they contain 82,576 sale records. Preserve these files unchanged for this project; do not replace them with later rolling downloads during the comparison.

`source_manifest.json` records the SHA256 checksum of each workbook. Original workbooks contain four introductory rows before the column headers; the notebook loads them with `header=4`.

The files are government source data. Refer to the source website for applicable terms; this repository does not assign a new license to those data.
