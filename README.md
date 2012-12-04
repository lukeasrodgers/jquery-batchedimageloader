Small plugin (about half a KB, minified) to batch load images to avoid
rate-limited image requests.

It works by splitting up the images into batches, then delayed-loading
them with setTimeout.

Developed for use with Google Contacts API which requires calls to image
resources to be authenticated with oauth access_token, but has an
(undocumented) rate limit of about 10 requests per second. 

This plugin ensures your images will eventually get loaded, avoiding 503
HTTP errors.

## Usage

Create markup like so (example uses Handlebars-style templating):

```
<img src="{default_picture}" alt="" width="48" height="48" class="batched-image-loader" data-img-src="{picture}" data-img-loaded="false" />
```

`default_picture` is optional, could be a default user avatar icon.
`picture` should be the real image source, provided by the Google API.

Then call batchedImageLoader() on the containing element:

```
$('#image-container').batchedImageLoader();
```

Options:

```javascript
$('#image-container').batchedImageLoader({
  delay: 1000, // in msecs
  batchSize: 10, // size of each batch to load
  className: 'batched-image-loader' // class on images
});
```
