# Campaigns

## List

```javascript
Mailshake.campaigns.list({
  search: 'Venkman'
})
  .then(result => {
    result.results.forEach(campaign => {
      console.log(JSON.stringify(campaign, null, 2));
    });
  })
  .catch(err => {
    console.error(`${err.code}: ${err.message}`);
  });
```

```shell
curl "https://api.mailshake.com/2017-04-01/campaigns/list" \
  -u "my-api-key:" \
  -d search=Venkman
```

> This endpoint returns [paginated](#Pagination) [Campaign](#Campaign) models.

List all of a team's campaigns.

### Parameters

Parameter | Default | Required | Description
--------- | ------- | -----------
search |  | No | Filters what campaigns are returned.
nextToken |  | No | Fetches the next page from a previous request.
perPage | 100 | No | How many campaigns to get at once, up to 100.

## Pause

```javascript
Mailshake.campaigns.pause({
  campaignID: 1
})
  .catch(err => {
    console.error(`${err.code}: ${err.message}`);
  });
```

```shell
curl "https://api.mailshake.com/2017-04-01/campaigns/pause" \
  -u "my-api-key:" \
  -d campaignID=1
```

> This endpoint returns an empty response.

Immediately pauses all sending for a campaign. If a batch of emails for this campaign is currently being sent they will not be stopped.

### Parameters

Parameter | Default | Required | Description
--------- | ------- | -----------
campaignID |  | Yes | The campaign to pause.

## Unpause

```javascript
Mailshake.campaigns.unpause({
  campaignID: 1
})
  .catch(err => {
    console.error(`${err.code}: ${err.message}`);
  });
```

```shell
curl "https://api.mailshake.com/2017-04-01/campaigns/unpause" \
  -u "my-api-key:" \
  -d campaignID=1
```

> This endpoint returns an empty response.

Immediately resumes sending for a campaign. This user's sending calendar will reschedule itself to account for this campaign's pending emails. In rare cases it may take up to 5 minutes for the calendar to show scheduled times for this campaign.

### Parameters

Parameter | Default | Required | Description
--------- | ------- | -----------
campaignID |  | Yes | The campaign to unpause.