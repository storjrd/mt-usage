# mt-usage

## 1. Install or include the Amazon S3 SDK.

e.g. with npm

```
npm install --save aws-sdk
```

## 2. Import the S3 client

``` javascript
import S3 from "aws-sdk/clients/s3";
```

## 3. Create client object with MT credentials

``` javascript
const accessKeyId = "access key here";
const secretAccessKey = "secret access key here";
const endpoint = "https://gateway.tardigradeshare.io";

const s3 = new S3({
  accessKeyId,
  secretAccessKey,
  endpoint,
  s3ForcePathStyle: true,
  signatureVersion: "v4",
  connectTimeout: 0,
  httpOptions: { timeout: 0 }
});
```

## 4. List objects and log to console

``` javascript
(async () => {

  const { Buckets } = await s3.listBuckets({}).promise();
  
  console.log(buckets);

})();
```

## 4. List objects and log to console

``` javascript
(async () => {

  const { Buckets } = await s3.listBuckets({}).promise();
  
  console.log(buckets);

})();
```
## 5. Upload an object

``` javascript
(async () => {

  // `file` can be a readable stream in node or a `Blob` in the browser

  const params = {
    Bucket: "my-bucket",
    Key: "my-object",
    Body: file
  };

  const upload = await s3.upload(params, {
    partSize: 64 * 1024 * 1024
  }).promise();
  
})();
