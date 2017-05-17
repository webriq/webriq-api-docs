---
title: WebriQ API Reference

language_tabs:
  - shell
  - javascript

toc_footers:
  - <a href="https://app.webriq.com/api/documentation#!/token/token" target="_blank">Get API Token</a>
  - <a href='https://app.webriq.com/api/documentation' target="_blank">Explore WebriQ API</a>
  - https://app.webriq.com/api

includes:
  - tokens
  - sites
  - responses

search: true
---

# Introduction

```shell
curl "https://app.webriq.com/api"
  -H "Authorization: Bearer <token>"
```

> Default API endpoint tells you the status of the API and its current version. Up and running response below:

```json
{
  "status": "OK",
  "version": "v1",
  "host": "https://app.webriq.com",
  "endpoints": {
    "sites": "https://app.webriq.com/api/sites"
  }
}
```

Welcome to the WebriQ API! You can use our API to access WebriQ API endpoints which allows you to view information of all your sites as well reading, putting, updating and deleting contents on your site.

We have language bindings in Shell and Javascript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/tripit/slate) and can be found at WebriQ's GitHub [repository](https://github.com/webriq/webriq-api-docs). Feel free to submit a pull request to help this documentation improve.

# Authentication

> To make authorized requests, use code below by passing the API token:

```shell
# With shell, you can just pass the correct header with each request
curl "https://app.webriq.com/api"
  -H "Authorization: Bearer <token>"
```

```javascript
const wapi = require('webriq-api');

let api = wapi.authorize('token');
```

> Make sure to replace `token` with your API key.

WebriQ API uses JSON Web Tokens to authorize access to the API. You can register a new WebriQ API by going to your sites settings page and `API` tab. Alternatively you can use the *Tokens* endpoint [below](#get-a-token) to generate one.

WebriQ API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer <token>`

<aside class="notice">
You must replace <code>&lt;token&gt;</code> with your personal API key.
</aside>
