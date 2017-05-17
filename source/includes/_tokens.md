## Get a Token

```shell
curl -X POST --header 'Content-Type: application/x-www-form-urlencoded' --header 'Accept: application/json' -d 'email=email@example.com&password=testpassword' 'https://app.webriq.com/api/token'
  -H "Authorization: Bearer <token>"
```

```javascript
const wapi = require('webriq-api');

let api = wapi.get('token');
```

> The above command returns JSON structured like this:

```json
{
  "message": "Token created successfully",
  "status": 200,
  "data": {
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjEsImlzcyI6Imh0dHBzOlwvXC93ZWJyaXEtcG9ydGFsLmRldlwvYXBpXC90b2tlbiIsImlhdCI6MTQ5NDgzNzg5MywiZXhwIjoxNDk0OTI0MjkzLCJuYmYiOjE0OTQ4Mzc4OTMsImp0aSI6ImQ3ZDkxOGI1YzFiODJiZTMyNWUxNzM0YjkxNDY3MTYwIn0.Rj_K78n03J2-FxEeM0-v4w2tkM_QPNiYmEK5Po2k2RQ"
  }
}
```

This endpoint provides basic authentication using user credentials and returns a JWT auth token that can be used on requests that needs authorization.

### HTTP Request

`POST https://app.webriq.com/api/token`


## Invalidate a Token

```shell
curl -X POST --header 'Content-Type: application/x-www-form-urlencoded' --header 'Accept: application/json' -d 'token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjEsImlzcyI6Imh0dHBzOlwvXC93ZWJyaXEtcG9ydGFsLmRldlwvYXBpXC90b2tlbiIsImlhdCI6MTQ5NDgzNzg5MywiZXhwIjoxNDk0OTI0MjkzLCJuYmYiOjE0OTQ4Mzc4OTMsImp0aSI6ImQ3ZDkxOGI1YzFiODJiZTMyNWUxNzM0YjkxNDY3MTYwIn0.Rj_K78n03J2-FxEeM0-v4w2tkM_QPNiYmEK5Po2k2RQ' 'https://app.webriq.com/api/token/invalidate
  -H "Authorization: Bearer <token>"
```

```javascript
const wapi = require('webriq-api');

let api = wapi.get('token').invalidate();
```

> The above command returns JSON structured like this:

```json
{
  "message": "Token invalidated successfully",
  "status": 200
}
```

This endpoint invalidates a previously generated token. Meaning, it can't be anymore used to further make authorized requests in behalf of your account.

### HTTP Request

`POST https://app.webriq.com/api/token/invalidate`



## Refresh a Token

```shell
curl -X GET --header 'Content-Type: application/x-www-form-urlencoded' --header 'Accept: application/json' 'https://app.webriq.com/api/token/refresh'
  -H "Authorization: Bearer <token>"
```

```javascript
const wapi = require('webriq-api');

let api = wapi.get('token').refresh();
```

> The above command returns JSON structured like this:

```json
{
  "message": "Token refreshed successfully",
  "status": 200,
  "data": {
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjEsImlzcyI6Imh0dHBzOlwvXC93ZWJyaXEtcG9ydGFsLmRldlwvYXBpXC90b2tlblwvcmVmcmVzaCIsImlhdCI6MTQ5NDgzMTg3NSwiZXhwIjoxNDk0OTI0OTIyLCJuYmYiOjE0OTQ4Mzg1MjIsImp0aSI6Ijk0NDY0ZmI2YzU0YzFiMDVmNzI4NjY0YjVkOTA5Mjk3In0.yIBFIzEky4IpftF5QHzIhzAigqmBBKkMbzNsA8OPxRA"
  }
}
```

This endpoint allows you to refresh the token.

### HTTP Request

`GET https://app.webriq.com/api/token/refresh`

### URL Parameters

Parameter | Description
--------- | -----------
token | Token to refresh
