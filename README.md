jquery-batchedimageloader
=========================

Small plugin to batch load images to avoid rate-limited image requests.

Developed for use with Google Contacts API which requires calls to image
resources to be authenticated with oauth access_token, but has an
(undocumented) rate limit of about 10 requests per second. 

This plugin ensures your images will eventually get loaded, avoiding 503
HTTP errors.
