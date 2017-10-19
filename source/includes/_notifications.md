# PING notifications

System sends ping notifications to your system on specified `Callback ping URL` after every asynchronous conversion. It is POST request and require HTTP 200-299 response to acknowledge. Any other HTTP response code will result in next trial schedule.

<aside class="warning">
System starts sending notification after all scheduled stages, for example if no cloud storage was selected ping will be send after conversion. If cloud storage was selected ping will be sent after uploading (or after trials limit, see Cloud Storage section)
</aside>

Notification parameters:

Parameter | Type | Description |
-------- | --------- | ---  |
conversion_id | string (UUID) | Conversion id
type | string ('sync', 'async') | Type of conversion. Currently only 'async' type is supported
status | string ('success', 'error') | Conversion result
notify_trial | integer | Number of ping trial. See below for timing table
storage | array | array of storage parameters, see below

Storage parameters:

Parameter | Type | Description |
trial | integer | Number of ping trial. See below for timing table
provider | string ('internal', 'gcs', 's3') | Cloud storage provider. `Internal` means storage in zone where document is processed, `gcs` is Google Cloud Storage, `s3` is Amazon S3
status | string ('success', 'error') | Upload result
error_code | integer | Error code of upload, see below
error_desc | string | Description of error. Field available when Cloud Storage returns error (only in `gcs` and 's3')
url | string | URL to converted file (only in `gcs` and 's3')
key | string | Object storage key (only in `gcs` and 's3')

Notification timing:

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

Error codes:

Code | Description |
-------- | --------- |
10 | Uploader temporary not available
11 | Cloud Storage error, description in error_desc field
12 | Cann not get credentials data
13 | General uploader error
14 | General uploader error
15 | General uploader error
