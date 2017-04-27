# Convert HTML/URL to PDF

### API endpoint

`POST https://[zone].pdfsquid.com/v1/[input_mode]/pdf/[sync]`

Parameter | Description
-------- | ---------
zone | zone name associated to api access
sync | if passed conversion will be synchronous, asynchronous is default
input_mode | source from where PDF will be produced. Can be `html` or `url`

All following parameters are supposed to be passed with POST method. For your convenience these are also grouped by functional context.

## Input source

Set accordingly to `input_mode` in API endpoint.

Parameter | Type | Required | Description |
-------- | --------- | -------- | ---  |
url | string | yes* | URL to website
html | string | yes* | HTML source

* means that one of the two (`url`, `html`) is required

## Metadata options

These will be visible in document properties.

Parameter | Type | Required | Description |
-------- | --------- | -------- | ---  |
title | string (0:64) | no | PDF title
subject | string (0:128) | no | PDF subject
author | string (0:64)| no | PDF author
creator | string (0:64) | no | PDF creator
producer | string (0:64) | no | PDF producer
keywords | string (0:256) | no | PDF keywords (comma separated)

## PDF options

Parameter | Type | Required | Description |
-------- | --------- | -------- | ---  |
margin-bottom | integer | no | PDF page bottom margin (mm), default 0 mm
margin-right | integer | no | PDF page right margin (mm), default 10 mm
margin-left | integer | no | PDF page left margin (mm), default 10 mm
margin-top | integer | no | PDF page top margin (mm), default 0 mm
orientation | string | no | PDF page orientation (`landscape` or `portrait`)
page-size | string | no | PDF page size (`A0`,`A1`,etc - look at ISO 216), default is `A4`
no-background | - | no | Do not print PDF page background
outline-depth | integer | no | Depth of the outline. Default is 4.
no-outline | - | no | Do not put an outline into the PDF. Default outline is present.
pdf-version | numeric (dot separated) | no | Set the desired PDF version

## Render options

Parameter | Type | Required | Description |
-------- | --------- | -------- | ---  |
disable-javascript | - | no | Disable javascript execution, default is enabled
watermark-url | string | no | Add watermark to every page. URL should point to image. The image will be streached to page size and centered.
watermark-opacity | numeric (dot separated) | no | Transparency of the watermark, where 1 means full opaque and 0 means full transparent. Default is 0.5.
watermark-position | string | no | Set the watermark position, could be `front` or `back`
convert-forms | - | no | Convert HTML form fields into PDF form fields. Default not converting.
viewport-size | string | no | Emulate passed window size (eg 1366x768)

## Header/footer

Parameter | Type | Required | Description |
-------- | --------- | -------- | ---
footer-html | string | no | HTML for footer
header-html | string | no | HTML for header
footer-line | - | no | Insert line between page content and footer, default not inserting
header-line | - | no | Insert line between page content and header, default not inserting
footer-spacing | integer | no | Footer margin from page content in mm, default `0`
header-spacing | integer | no | Header margin from page content in mm, default `0`
footer-without-pages | string | no | Specify pages without footer, separated by comma
header-without-pages | string | no | Specify pages without header, separated by comma

<aside class="notice">
In footer-html and header-html you can use `{page}` and `{pages}` variables which will be replaced by current page and all pages respectively
</aside>

## Encryption options

Parameter | Type | Required | Description |
-------- | --------- | -------- | ---  |
pdf-key-length | integer | no | Set PDF encryption key length (40, 128, 256)
pdf-user-password | string (0:64) | no* | Set user password (cannot manage permissions, strict rights access)
pdf-owner-password | string (0:64) | no* | Set owner password (full permission management)
pdf-print | string (yes|no) | no | Set print permission, default yes
pdf-modify | string (yes|no) | no | Used if pdf-key-length is 40. Turn on/off ability to modify.
pdf-annotate | string (yes|no) | no | Used if pdf-key-length is 40. Turn on/off ability to comment, form fill-in and signing.
pdf-modify-opt | string | no | Set modification permissions. Values: `all`,`annotate` (allow comment authoring and form operations), `form` (allow form field fill-in and signing), `assembly` (allow document assembly only), `none`. Values `form` and `assembly` require `pdf-key-length` >= `128`. Default `all`.
pdf-extract | string (yes|no) | no | Allow text/graphic extraction, default `yes`
pdf-cleartext-metadata | - | no | Prevents encryption of metadata. Default metadata is encrypted. Available if `pdf-key-length` >= `128`.

* If setting password both pdf-user-password and pdf-owner-password must be set

<aside class="notice">
Specifying pdf-cleartext-metadata forces the PDF version to at least 1.5.
If pdf-key-length is 256, the PDF version will be at least 1.6.
</aside>

## Request propagation/authentication

Warning: This section applies to URL conversion only!

Parameter | Type | Required | Description |
-------- | --------- | -------- | ---  |
pass-post | string-json | no | Key-valued json string with POST data to be passed to URL
pass-headers | string-json | no | Key-valued json string with headers data to be passed to URL. User-Agent is restricted. These headers will be propagated to every request (eg. images)!
pass-cookies | string-json | no | Key-valued json string with cookies data to be passed to URL
http-user | string (0:128) | no | Basic HTTP authentication user
http-password | string (0:128) | no | Basic HTTP authentication password

<aside class="notice">
Custom User-Agent in headers propagation is NOT supported
</aside>
