# mt-usage

* Install or include the Amazon S3 SDK.

e.g. install with npm

```
npm install --save aws-sdk
```

* Import the S3 client

``` javascript
import S3 from "aws-sdk/clients/s3";
```

* Create client object with MT credentials

``` javascript
const accessKeyId = "access key here";
const secretAccessKey = "secret access key here";

const s3 = new S3({
  accessKeyId,
  secretAccessKey,
  endpoint: "https://gateway.tardigradeshare.io",
  s3ForcePathStyle: true,
  signatureVersion: "v4"
});
```

* List objects and log to console

```
(async () => {

  const { Buckets } = await s3.listBuckets({}).promise();
  
  console.log(buckets);

})();

```
