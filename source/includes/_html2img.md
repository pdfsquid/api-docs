# Convert HTML/URL to image

### API endpoint

`POST https://[zone].pdfsquid.com/v1/[html|url]/img/[sync]`

Parametr | Description
-------- | ---------
zone | zone name associated to api access
sync | if passed conversion will be synchronous, asynchronous is default


## Source definition

Parametr | Type | Required | Description |
-------- | --------- | -------- | ---  |
url | string | yes* | URL to website
html | string | yes* | HTML source

* means that one of the two (`url`, `html`) is required 

## Image format

Parametr | Type | Required | Description |
-------- | --------- | -------- | ---  |
format | string (jpg|png) | no | Image format, default jpg
crop-h | integer | no | Set height for croping
crop-w | integer | no | Set width for croping
crop-x | integer | no | Set x coordinate for croping
crop-y | integer | no | Set y coordinate for croping
quality | integer | no | Output image quality (0-100), default 94

## Render options

Parametr | Type | Required | Description |
-------- | --------- | -------- | ---  |
disable-javascript | - | no | Disable javascript execution, default is enabled
watermark-url | string | no | Add watermark to every page. URL should point to image. The image will be streached to page size and centered.
watermark-opacity | numeric (dot separated) | no | Transparency of the watermark, where 1 means full opaque and 0 means full transparent
watermark-position | string | no | Set the watermark position, could be `front` or `back`

## Request propagation/authentication

Warning: This section applies to URL convertion only!

Parametr | Type | Required | Description |
-------- | --------- | -------- | ---  |
pass-post | string-json | no | Key-valued json string with POST data to be passed to URL
pass-headers | string-json | no | Key-valued json string with headers data to be passed to URL. User-Agent is restricted. These headers will be propagated to every request (eg. images)!
pass-cookies | string-json | no | Key-valued json string with cookies data to be passed to URL
http-user | string (0:128) | no | Basic HTTP authentication user
http-password | string (0:128) | no | Basic HTTP authentication password

<aside class="notice">
Custom User-Agent in headers propagation is NOT supported
</aside>

