# Introduction

> **API Endpoint**
> <code>https<span></span>://api.mailshake.com/2017-04-01</code>

Thank you for checking out the Mailshake API! We ♥️ devs because that's who we are, so we hope you'll find our API enjoyable. If you notice a typo or have a suggestion on making this documentation better, just open up a pull request on [the repository that runs this site](https://github.com/colinmathews/mailshake-api-docs) and we'll check it out.

You'll interact with the Mailshake API by making `GET` or `POST` requests (`POST` is recommended when sending larger payloads). All responses are JSON-formatted, and each application has its own quota limits based on your Mailshake subscription.

## Making requests

When making a `POST` request you can send content as a typical form payload by using the header:

`Content-Type: application/x-www-form-urlencoded`

or you can write JSON data to the request by using the header:

`Content-Type: application/json`

See [authentication](#Authentication) for examples of how to make requests.

## Responses

> Single-item responses will be in this format:

```json
{
  "object": "campaign",
  "id": 1,
  "title": "My campaign",
  "created": "2017-08-19T02:31:22.218Z"
}
```

Most endpoints return a single model of data. Check out our [models section](#Models) for specific examples and be sure to check out the [errors section](#Errors) section, too.

### Common fields

Field | Type | Description
--------- | ------- | -----------
object | string | The type of model this data represents.
id | integer | The unique ID of this data.

## Pagination

> Paginated data will look like this:

```json
{
  "nextToken": "...",
  "results": [
    { ... },
    { ... }
  ]
}
```

> Get the next page of data like so:

```javascript
request('campaigns/list', {
  nextToken: '...'
});
```

```shell
curl "https://api.mailshake.com/2017-04-01/campaigns/list?nextToken=..." \
  -u "my-api-key:"
```

Endpoints that return multiple results will include a `nextToken` parameter that you can pass into another request to fetch the next results. These endpoints will also accept a `perPage` parameter to control the size of the record sets.