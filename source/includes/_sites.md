# Sites





################################################################################################################################################################################
## Get All Sites

```shell
curl "https://app.webriq.com/api/sites"
  -H "Authorization: Bearer <token>"
```

```javascript
const wapi = require('webriq-api');

let api = wapi.authorize('token');
let sites = api.sites.get();
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "EKekWeRrRqPQ",
      "primary_owner": "hellome@gmail.com",
      "role": "owner",
      "subdomain": "anewsitehasbeenmade.sites.webriqs.com",
      "domains": [
        "gel.com"
      ],
      "active": true,
      "secured": false,
      "force_secured": false,
      "created": "2017-03-15T07:08:25+00:00",
      "updated": "2017-03-15T07:08:25+00:00",
      "endpoints": {
        "collections": "https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections"
      }
    },
    {...},
    {...},
    {...}
  ]
}
```

This endpoint retrieves all sites on your WebriQ account. Sites you <code>primarily owned</code>, <code>invited to owned</code> and/or with you as <code>developer</code>. The rest of the API endpoints will allow you to see how the data model is designed on your site as well as be able to read, create, update, delete data/content saved.

### HTTP Request

`GET https://app.webriq.com/api/sites`





################################################################################################################################################################################
## Get Site

```shell
curl "https://app.webriq.com/api/sites/EKekWeRrRqPQ"
  -H "Authorization: Bearer <token>"
```

```javascript
const wapi = require('webriq-api');

let api = wapi.authorize('token');
let site = api.sites.get('EKekWeRrRqPQ');
```


> The above command returns JSON structured like this:

```json
{
  "data": {
    "collections": "https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections"
  },
  "status_code": 200
}
```

This endpoint retrieves all available site API endpoints for a given site by passing its ID. By default, this returns the `collection` API endpoint.

### HTTP Request

`GET https://app.webriq.com/api/sites/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the site to retrieve





################################################################################################################################################################################
## Get Site Collection Model

```shell
curl "https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections"
  -H "Authorization: Bearer <token>"
```

```javascript
const wapi = require('webriq-api');

let api = wapi.authorize('token');
let site_collection_model = api.sites.get('EKekWeRrRqPQ').collections;
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "name": "sitedata",
      "label": "Site Information",
      "type": "file",
      "endpoints": [
        "https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections/sitedata"
      ]
    },
    {
      "name": "slider",
      "label": "Image Slider",
      "type": "file",
      "endpoints": [
        "https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections/slider"
      ]
    },
    {
      "name": "services",
      "label": "Services",
      "type": "folder",
      "endpoints": [
        "https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections/services"
      ]
    },
    {
      "name": "work",
      "label": "Featured Work",
      "type": "folder",
      "endpoints": [
        "https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections/work"
      ]
    },
    {
      "name": "news",
      "label": "News",
      "type": "folder",
      "endpoints": [
        "https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections/news"
      ]
    },
    {
      "name": "testi",
      "label": "Testimonial",
      "type": "file",
      "endpoints": [
        "https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections/testi"
      ]
    },
    {
      "name": "data",
      "label": "Partners Logo",
      "type": "file",
      "endpoints": [
        "https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections/data"
      ]
    }
  ],
  "status_code": 200
}
```

This endpoint retrieves the summary of the data model of the current site. This data model tells us which parts of your site's data we can work on; activities such as creating, reading, updating, deleting content and more.

### HTTP Request

`GET https://app.webriq.com/api/sites/<ID>/collections`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the site to retrieve

<aside class="notice">
A <code>collection</code> is a simple group of data via a definition or a model. There are two types of collection, <code>file</code> and <code>folder</code>. Folder houses a list of <code>files</code> or <code>folder</code> types. In the end, the very basic type of <code>file</code> is the resource where you can work on saving, updating and deleting data.
</aside>






################################################################################################################################################################################
## Get Site Collection

```shell
# FILE TYPE

curl "https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections/news/2016-04-04-working-with-json.md"
  -H "Authorization: Bearer <token>"

# FOLDER TYPE

curl "https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections/news"
  -H "Authorization: Bearer <token>"
```

```javascript
// FILE TYPE

const wapi = require('webriq-api');

let api = wapi.authorize('token');
let site = api.sites.get('EKekWeRrRqPQ').collections.get('news/2016-04-04-working-with-json.md');

// FOLDER TYPE

const wapi = require('webriq-api');

let api = wapi.authorize('token');
let site = api.sites.get('EKekWeRrRqPQ').collections.get('news');
```

> Example result below for <code>file</code> type

```json
{
  "data": {
    "title": "Working With JSON",
    "date": 1459900800,
    "shortdesc": "Here is some more information about this product that is only revealed once clicked on.",
    "banner": "/img/article3.jpg",
    "categories": "technology food",
    "body": "[Finn](http://adventuretime.wikia.com/wiki/Finn) and [Jake](http://adventuretime.wikia.com/wiki/Jake) hitch a ride on a Citadel Guardian after he imprisons and transports [The Lich](http://adventuretime.wikia.com/wiki/The_Lich_(character)) to the Citadel. Upon arrival, the Guardian attaches The Lich's crystal prison onto a much larger crystal \"cell block.\" Finn then says it is a good riddance for The Lich.<!--more--> As they talk, The Lich begins emitting a gray breath in his cell which the duo don't notice. Finn and Jake then look around for Finn's long-lost father, whom Finn initially suggests might be a Guardian. Jake points out a strange looking \"old kid\" who resembles Finn, and it turns out to be Finn's father incarcerated inside a crystal jail cell.\n\nFinn runs to his dad and looks him closely. A gray slime fire forms on Finn's father's cell, which makes Finn hyper about it and asks Jake about the fire. Jake then points above from where the fire had fallen on the cell. They then notice that the Lich's cell is excreting a gray slime that is beginning to infect the other prisoners and making them under the influence of The Lich. The cell of Finn's father then melts and his father half inside the cell asks Finn for help. Finn uses Jake as flail to break him out of the cell. The Lich's influence over the Citadel enables a massive jailbreak. \n\nFinn's father then asks him about the \"starskipper\" from which they came, completely ignoring the fact that there is another human in his presence. The prisoners are running amok and attacking the Guardians and making each other gray. After Jake says that Finn is his son, Finn's father is still not surprised by it and starts telling them to find a way to escape. Finn starts to ask his father why he abandoned him, but before he could do, his father jumps in the center of the Citadel, as the ground was melting."
  },
  "status_code": 200
}
```

> Example result below for <code>folder</code> type

```json
{
  "data": [
    {
      "name": "2016-04-04-working-with-json.md",
      "path": "news/2016-04-04-working-with-json.md",
      "sha": "21400d0f6e60399082e167da808c3f76e28f1b2f",
      "type": "file"
    },
    {
      "name": "2016-04-05-Materialize.md",
      "path": "news/2016-04-05-Materialize.md",
      "sha": "8bb7b505217eea6ebd9381943f8ff31d4500eba8",
      "type": "file"
    },
    {
      "name": "2016-04-06-get-your-rating-widget-now.md",
      "path": "news/2016-04-06-get-your-rating-widget-now.md",
      "sha": "b0abe551ca221ebea7e6261ba3804341937d82b2",
      "type": "file"
    },
    {...},
    {...},
    {...}
  ],
  "status_code": 200
}
```

This endpoint retrieves the collection data of the current collection.

### HTTP Request

`GET https://app.webriq.com/api/sites/<ID>/collections/<COLLECTION_NAME>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the site to retrieve
COLLECTION_NAME | The name of the Collection

<aside class="notice">
A `collection` is a simple group of data via a definition or a model. There are two types of collection, <code>file</code> and <code>folder</code>. Folder may consist of files and folder with files inside.
</aside>





################################################################################################################################################################################
## Save New Site Collection

```shell
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' -d '{ \
     "title": "Working With JSON", \
     "date": "1459900800", \
     "shortdesc": "Here is some more information about this product that is only revealed once clicked on.", \
     "banner": "/img/article3.jpg", \
     "categories": "technology food", \
     "body": "Sample markdown content" \
   }' 'https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections/news%2Fsamplemarkdown22.md'
  -H "Authorization: Bearer <token>"
```


```javascript
const wapi = require('webriq-api');

let api = wapi.authorize('token');
let site = api.sites.get('EKekWeRrRqPQ').collections.post('news/samplemarkdown22.md').data({
  "title": "Working With JSON",
  "date": "1459900800",
  "shortdesc": "Here is some more information about this product that is only revealed once clicked on.",
  "banner": "/img/article3.jpg",
  "categories": "technology food",
  "body": "Sample markdown content"
});
```

> The above command returns JSON structured like this:

```json
{
  "message": "Collection created at 'news/samplemarkdown22.md'",
  "data": {
    "main": {
      "title": "Working With JSON",
      "date": "1459900800",
      "shortdesc": "Here is some more information about this product that is only revealed once clicked on.",
      "banner": "/img/article3.jpg",
      "categories": "technology food",
      "body": "Sample markdown content"
    },
    "uploads": []
  },
  "status_code": 201
}
```

This endpoint saves a given collection of a given site. The retrieved collection model must be followed in JSON format and passed in the body section.

### HTTP Request

`POST https://app.webriq.com/api/sites/<ID>/collections/<COLLECTION_PATH_AND_NAME>`

### URL Parameters

Parameter | Description | Location
--------- | ----------- | ---------
ID | The ID of the site | Query URL
COLLECTION_PATH_AND_NAME | Collection name and path to save | Query URL
BODY | JSON Raw Data | Request Body following the Collection model




################################################################################################################################################################################
## Update Existing Collection

```shell
curl -X PUT --header 'Content-Type: application/json' --header 'Accept: application/json' -d '{ \
     "title": "Working With JSON", \
     "date": "1459900800", \
     "shortdesc": "Here is some more information about this product that is only revealed once clicked on.", \
     "banner": "/img/article3.jpg", \
     "categories": "technology food", \
     "body": "Sample update markdown content" \
   }' 'https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections/news%2Fsamplemarkdown22.md'
  -H "Authorization: Bearer <token>"
```


```javascript
const wapi = require('webriq-api');

let api = wapi.authorize('token');
let site = api.sites.get('EKekWeRrRqPQ').collections.put('news/samplemarkdown22.md').data({
  "title": "Working With JSON",
  "date": "1459900800",
  "shortdesc": "Here is some more information about this product that is only revealed once clicked on.",
  "banner": "/img/article3.jpg",
  "categories": "technology food",
  "body": "Sample update markdown content"
});
```

> The above command returns JSON structured like this:

```json
{
  "message": "Collection updated at 'news/samplemarkdown22.md'",
  "data": {
    "main": {
      "title": "Working With JSON",
      "date": "1459900800",
      "shortdesc": "Here is some more information about this product that is only revealed once clicked on.",
      "banner": "/img/article3.jpg",
      "categories": "technology food",
      "body": "Sample update markdown content"
    },
    "uploads": []
  },
  "status_code": 200
}
```

This endpoint updates a given collection of a given site. The retrieved collection model must be followed in JSON format and passed in the body section.

### HTTP Request

`POST https://app.webriq.com/api/sites/<ID>/collections/<COLLECTION_PATH_AND_NAME>`

### URL Parameters


Parameter | Description | Location
--------- | ----------- | ---------
ID | The ID of the site | Query URL
COLLECTION_PATH_AND_NAME | Collection name and path to save | Query URL
BODY | JSON Raw Data | Request Body following the Collection model





##################################################################################################################################################################################
## Deleting Collection

```shell
curl -X DELETE --header 'Accept: application/json'
  'https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections/news%2Fsamplemarkdown22.md'
  -H "Authorization: Bearer <token>"
```

```javascript
const wapi = require('webriq-api');

let api = wapi.authorize('token');
let site = api.sites.get('EKekWeRrRqPQ').collections.delete('news/samplemarkdown22.md');
```

> The above command returns JSON structured like this:

```json
{
  "status_code": 200,
  "data": null
}
```

This endpoint deletes a given collection of a given site by passing its path and name.

### HTTP Request

`DELETE https://app.webriq.com/api/sites/<ID>/collections/<COLLECTION_PATH_AND_NAME>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the site
COLLECTION_PATH_AND_NAME | Collection name and path to save





################################################################################################################################################################################
## File Uploads

```shell
# POST and PUT requests are allowed for file uploads
curl -X PUT --header 'Content-Type: application/json' --header 'Accept: application/json' -d '{ \
     "title": "Working With JSON", \
     "date": "1459900800", \
     "shortdesc": "Here is some more information about this product that is only revealed once clicked on.", \
     "banner": { \
        "filedata": { \
          "name": "11111.png", \
          "content": "iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTRGQjkwNjdERjk1MTFFNUFFNzE5NDRDRDE3NUExN0YiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTRGQjkwNjhERjk1MTFFNUFFNzE5NDRDRDE3NUExN0YiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNEZCOTA2NURGOTUxMUU1QUU3MTk0NENEMTc1QTE3RiIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNEZCOTA2NkRGOTUxMUU1QUU3MTk0NENEMTc1QTE3RiIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PmXj5kYAAAN5SURBVHja7JdJaFRBEIbnDYlOVvctalCj4oIhUUGQHBSFJO6CB4MgKJ4UQtCLXiTEKBEVUUGCGggu4EFRvLgvmAWNSzQqxgUMUXHFaBRNXDL+hf+Dou15b0aFudjw8eZ1VVfX666u6nHC4XAgni0YiHOLuwMJXkLHcRLxGAemgElgFBgCeoMkpdoJ3oOX4DG4Da6CW9jiT55z2GIAEw/HowgsArlK1AaegjfgA/gh6iAN9AJDwSCl3wKOgWrM02T1QBxw4ZdtBO0iAq9lMFhKR2SSoB5jjE8Bo8E8sA3cpx1xdKs4+tsYw8BZDmgEy0G/SJNFA1oIzAG1tLvXz4EOcBEkG/1JMUwqcdPd4sgD8NDUN0+BaLdA8FnFw3o86vEsAUGfoJ2FRx2owe+Raps7uJ2O3yn4xjjQTQIyh2SC1REmL8DjKL9WWg8lC9Juh18QPpGvNfok8I5zdYSFlmWXyG+l/B6YbcjTeYLO+cXABfAWpBr93cBOTnBd9tmQuzIJtkyLg+Mpr/RzYAsVcy1GeoIzlOep/mFAks1dHtcSy9jFHLfCLwgv8Zln2eZycBJIgOar/vk8/yv5PsMyNp8O1PnVgnrwjh6bbTJ4BQ6C6ap/AWjA11xmqg4ZwSkrN1fSMnjk6QCMtDF1TsXAXMuJkWNUKfsMeTpI5f7uoU4Gv1Q3mbwPOAT736Ophq6xYkuOkOBrZNGRIjUYiNFT6uglGMWsBHwEh6Mtx9fAabAEBrJpyOHXu4mkAUwEY0EznHrO/mRJ39QPsJiJXpXS8XYg/CtsS5lSK1RfAouKtPNMTNlM3W4LMVmlwAepkBtYprfHdCHBfFekcIBCGCrmF/VVmayJ9wK5J9xQQxOZdGRr1oIssAn2WiPmb4+i0p+Z8QtYw/pfQFkaK6YE7Rg1po6xsp+xUW8WJs9EZHGiUKXgr7Kf7A/y1iPLO0Dp1yh9cW6CX/X0rG5QkMSzDnTRaDv7u5j92rkybnumTswq6N3xvRRGUd9HcDJ5OSJ1gf0VPNsBtS3uFpRFfX+IwoFSGnVXodq9dMi5p06GqhM7vK5tscbAQPCChneDffx9QK2EpOhm9u+K+drm48BmFVTTmIiq+H4CLGPtkPfyP7o3ekyexft+mJkvpGRlyrFOW5n9Fw7I8t9kosmxyIu47zP/5ubs/P9zGm8HfgowAOu/JVc3mQ8hAAAAAElFTkSuQmCC" \
        } \
      }, \
     "categories": "technology food", \
     "body": "Sample update markdown content" \
   }' 'https://app.webriq.com/api/sites/EKekWeRrRqPQ/collections/news%2Fsamplemarkdown22.md'
  -H "Authorization: Bearer <token>"
```

```javascript
const wapi = require('webriq-api');

let api = wapi.authorize('token');
let site = api.sites.get('EKekWeRrRqPQ').collections.post('news/samplemarkdown22.md').data({
  "title": "Working With JSON",
  "date": "1459900800",
  "shortdesc": "Here is some more information about this product that is only revealed once clicked on.",
  "banner": {
    "filedata": {
      "name": "11111.png",
      "content": "iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTRGQjkwNjdERjk1MTFFNUFFNzE5NDRDRDE3NUExN0YiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTRGQjkwNjhERjk1MTFFNUFFNzE5NDRDRDE3NUExN0YiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNEZCOTA2NURGOTUxMUU1QUU3MTk0NENEMTc1QTE3RiIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNEZCOTA2NkRGOTUxMUU1QUU3MTk0NENEMTc1QTE3RiIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PmXj5kYAAAN5SURBVHja7JdJaFRBEIbnDYlOVvctalCj4oIhUUGQHBSFJO6CB4MgKJ4UQtCLXiTEKBEVUUGCGggu4EFRvLgvmAWNSzQqxgUMUXHFaBRNXDL+hf+Dou15b0aFudjw8eZ1VVfX666u6nHC4XAgni0YiHOLuwMJXkLHcRLxGAemgElgFBgCeoMkpdoJ3oOX4DG4Da6CW9jiT55z2GIAEw/HowgsArlK1AaegjfgA/gh6iAN9AJDwSCl3wKOgWrM02T1QBxw4ZdtBO0iAq9lMFhKR2SSoB5jjE8Bo8E8sA3cpx1xdKs4+tsYw8BZDmgEy0G/SJNFA1oIzAG1tLvXz4EOcBEkG/1JMUwqcdPd4sgD8NDUN0+BaLdA8FnFw3o86vEsAUGfoJ2FRx2owe+Raps7uJ2O3yn4xjjQTQIyh2SC1REmL8DjKL9WWg8lC9Juh18QPpGvNfok8I5zdYSFlmWXyG+l/B6YbcjTeYLO+cXABfAWpBr93cBOTnBd9tmQuzIJtkyLg+Mpr/RzYAsVcy1GeoIzlOep/mFAks1dHtcSy9jFHLfCLwgv8Zln2eZycBJIgOar/vk8/yv5PsMyNp8O1PnVgnrwjh6bbTJ4BQ6C6ap/AWjA11xmqg4ZwSkrN1fSMnjk6QCMtDF1TsXAXMuJkWNUKfsMeTpI5f7uoU4Gv1Q3mbwPOAT736Ophq6xYkuOkOBrZNGRIjUYiNFT6uglGMWsBHwEh6Mtx9fAabAEBrJpyOHXu4mkAUwEY0EznHrO/mRJ39QPsJiJXpXS8XYg/CtsS5lSK1RfAouKtPNMTNlM3W4LMVmlwAepkBtYprfHdCHBfFekcIBCGCrmF/VVmayJ9wK5J9xQQxOZdGRr1oIssAn2WiPmb4+i0p+Z8QtYw/pfQFkaK6YE7Rg1po6xsp+xUW8WJs9EZHGiUKXgr7Kf7A/y1iPLO0Dp1yh9cW6CX/X0rG5QkMSzDnTRaDv7u5j92rkybnumTswq6N3xvRRGUd9HcDJ5OSJ1gf0VPNsBtS3uFpRFfX+IwoFSGnVXodq9dMi5p06GqhM7vK5tscbAQPCChneDffx9QK2EpOhm9u+K+drm48BmFVTTmIiq+H4CLGPtkPfyP7o3ekyexft+mJkvpGRlyrFOW5n9Fw7I8t9kosmxyIu47zP/5ubs/P9zGm8HfgowAOu/JVc3mQ8hAAAAAElFTkSuQmCC"
    }
  },
  "categories": "technology food",
  "body": "Sample markdown content"
});
```

> The above command returns JSON structured like this:

```json
{
  "message": "Collection updated at 'news/2016-04-04-working-with-json.md'",
  "data": {
    "main": {
      "title": "Working With JSON",
      "date": "1459900800",
      "shortdesc": "Here is some more information about this product that is only revealed once clicked on.",
      "banner": "img/11111.png",
      "categories": "technology food",
      "body": "Sample update markdown content"
    },
    "uploads": [
      {
        "key_path": "banner",
        "content": "iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTRGQjkwNjdERjk1MTFFNUFFNzE5NDRDRDE3NUExN0YiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTRGQjkwNjhERjk1MTFFNUFFNzE5NDRDRDE3NUExN0YiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNEZCOTA2NURGOTUxMUU1QUU3MTk0NENEMTc1QTE3RiIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNEZCOTA2NkRGOTUxMUU1QUU3MTk0NENEMTc1QTE3RiIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PmXj5kYAAAN5SURBVHja7JdJaFRBEIbnDYlOVvctalCj4oIhUUGQHBSFJO6CB4MgKJ4UQtCLXiTEKBEVUUGCGggu4EFRvLgvmAWNSzQqxgUMUXHFaBRNXDL+hf+Dou15b0aFudjw8eZ1VVfX666u6nHC4XAgni0YiHOLuwMJXkLHcRLxGAemgElgFBgCeoMkpdoJ3oOX4DG4Da6CW9jiT55z2GIAEw/HowgsArlK1AaegjfgA/gh6iAN9AJDwSCl3wKOgWrM02T1QBxw4ZdtBO0iAq9lMFhKR2SSoB5jjE8Bo8E8sA3cpx1xdKs4+tsYw8BZDmgEy0G/SJNFA1oIzAG1tLvXz4EOcBEkG/1JMUwqcdPd4sgD8NDUN0+BaLdA8FnFw3o86vEsAUGfoJ2FRx2owe+Raps7uJ2O3yn4xjjQTQIyh2SC1REmL8DjKL9WWg8lC9Juh18QPpGvNfok8I5zdYSFlmWXyG+l/B6YbcjTeYLO+cXABfAWpBr93cBOTnBd9tmQuzIJtkyLg+Mpr/RzYAsVcy1GeoIzlOep/mFAks1dHtcSy9jFHLfCLwgv8Zln2eZycBJIgOar/vk8/yv5PsMyNp8O1PnVgnrwjh6bbTJ4BQ6C6ap/AWjA11xmqg4ZwSkrN1fSMnjk6QCMtDF1TsXAXMuJkWNUKfsMeTpI5f7uoU4Gv1Q3mbwPOAT736Ophq6xYkuOkOBrZNGRIjUYiNFT6uglGMWsBHwEh6Mtx9fAabAEBrJpyOHXu4mkAUwEY0EznHrO/mRJ39QPsJiJXpXS8XYg/CtsS5lSK1RfAouKtPNMTNlM3W4LMVmlwAepkBtYprfHdCHBfFekcIBCGCrmF/VVmayJ9wK5J9xQQxOZdGRr1oIssAn2WiPmb4+i0p+Z8QtYw/pfQFkaK6YE7Rg1po6xsp+xUW8WJs9EZHGiUKXgr7Kf7A/y1iPLO0Dp1yh9cW6CX/X0rG5QkMSzDnTRaDv7u5j92rkybnumTswq6N3xvRRGUd9HcDJ5OSJ1gf0VPNsBtS3uFpRFfX+IwoFSGnVXodq9dMi5p06GqhM7vK5tscbAQPCChneDffx9QK2EpOhm9u+K+drm48BmFVTTmIiq+H4CLGPtkPfyP7o3ekyexft+mJkvpGRlyrFOW5n9Fw7I8t9kosmxyIu47zP/5ubs/P9zGm8HfgowAOu/JVc3mQ8hAAAAAElFTkSuQmCC",
        "media_folder": "assets/img",
        "filename": "11111.png"
      }
    ]
  },
  "status_code": 200
}
```

When working with file uploads, you can directly upload files via attaching the raw data of file in JSON format. File uploads only works on data type <code>image</code>.

One should follow the format below:

<code>
"filedata": {
  "name": "filename.png",
  "content": "base64_encoded_data"
}
</code>

In **Save New Site Collection** example POST request via <code>shell</code>, we can only do file upload on <code>banner</code> key as it's the only one with <code>image</code> data type.

### HTTP Request

`POST https://app.webriq.com/api/sites/<ID>/collections/<COLLECTION_PATH_AND_NAME>`

`PUT https://app.webriq.com/api/sites/<ID>/collections/<COLLECTION_PATH_AND_NAME>`

### URL Parameters

Parameter | Description | Location
--------- | ----------- | ---------
ID | The ID of the site | Query URL
COLLECTION_PATH_AND_NAME | Collection name and path to save | Query URL
BODY | JSON Raw Data | Request Body following the Collection model

<aside class="notice">
File upload <code>content</code> must be <code>base64 encoded</code>. Find out how to get base64 encoded data with your choice of language.
</aside>
