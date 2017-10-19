# Examples

## Footer/header HTML

This is samle footer with dynamic page evaluation. Take a notice of mandatory `<!DOCTYPE html>`.

```html
<!DOCTYPE html>
<html>
<body style="text-align:center;">
	<h3>Sample footer on page {page}/{pages}</h3>
</body>
</html>
```

## Page composition

PDFsquid supports page break controlling feature. In your HTML code just add any of the following css attributes:

Parameter | Possible values | Description
----------|-----------------|-----------|
page-break-after | auto, always, avoid | Controls page break behavior after this HTML tag
page-break-before | auto, always, avoid | Controls page break behavior before this HTML tag
page-break-inside | auto | avoid | Controls page break behavior on this HTML tag. Useful in case of long content (eg. table) which has to be on one page as a whole

Example:

```html
<h1>Page 1<h1>
<h1 style="page-break-before:always">Page 2<h1>
```
