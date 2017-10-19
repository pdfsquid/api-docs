# Document storage

This section applies to asynchronous conversions only.

PDFsquid supports following storage providers:

- Amazon S3 (s3)
- Google Cloud Storage (gcs)
- Internal

## Cloud storage providers

For s3 and gcs storage converted files are uploaded to specified buckets defined in dashboard. You can download them after receiving ping notification or try direct download (take into account that without ping you do not really know when the file will be available). Key for object file will be:
conversion id + '.' + file format (pdf, png, jpg)
for example:
`43fd74e5-bee0-4bac-a356-ba57a0a6b540.pdf`

If any error occurs during uploading, following upload trial table applies:

Trial | Time to next trial |
-------- | --------- |
1 | - (instant)
2 | 1 min
3 | 3 min
4 | 10 min
5 | 15 min
6 | 30 min
7 | 60 min
8 | 180 min (3h)
9 | 360 min (6h)
10 | 720 min (12h)
11 | 1440 (24h)

## Internal storage

To download file from internal storage perform following API request:

`POST https://[zone].pdfsquid.com/v1/getfile/[conversion_id]`

Response headers:

Header name | value
-------- | --------- |
content-disposition | attachment; filename=[conversion_id].[file_format]
content-transfer-encoding | binary
content-type | [according content type for file format]
output-format | [file_format]
conversion-id | [conversion_id]

File will be removed after 48 hours from conversion or after downloading.
