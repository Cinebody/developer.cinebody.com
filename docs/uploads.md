# Video Uploads

You can upload clips on behalf of a user by calling the upload endpoints. We use multipart uploads which means files are uploaded in chunks. This allows very large files to be uploaded and we can support features like retry on failure.

An upload consists of 3 steps:

1. Request the upload URLs
2. `PUT` the file chunks to the upload urls
3. Call the "complete upload" endpoint with ETags to finalize the upload

## Step 1: Request the upload URLs

![Request upload URLs](/assets/get-upload-url.jpg)

The response contains an array of `signedUrls` where you will upload the chunks. The `chunkSizeBytes` tells you how big each file chunk should be.

_Note: The last file chunk is whatever is left and the size will be less than the `chunkSizeBytes`_

## Step 2: Upload each chunk

![Upload parts](/assets/upload-parts-params.jpg)

The signed url you got from step 1 is used and you'll `PUT` the chunk to that url. You'll need to keep track of the `uploadId` (same for all chunks), `partNumber`, and `ETag` for use in the next step.

## Step 3: Complete the upload

Finally, you'll tell the api that you've finished uploading all the file chunks. The file will be re-assembled and transcoded at this point.

As part of this call, you must specify a `userId`. The clip will be associated to that user just as if they had manually uploaded the file on [pro.cinebody.com](https://pro.cinebody.com).

![Complete upload](/assets/complete-upload.jpg)

## Troubleshooting

The most common error is receiving a `SignatureDoesNotMatch` error when uploading a chunk.
* Make sure that you are not sending any extraneous headers
* Make sure the Content-Length matches the size of the chunk you are sending

