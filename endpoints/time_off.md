# Time Off

## Get Downtimes

* `GET /v1/:subdomain/downtimes` returns an `Array` of **Downtimes**.

### Query String Parameters

Parameter | Default | Description
--- | --- | --- | ---
resource_ids | | Limit the number of results 
from | | Set a start date range for downtimes
to | | Set an end date range for downtimes

**Example:**

```
https://api.resourceguruapp.com/v1/example-corp/downtimes?from=2016-02-16&to=2016-02-22
```
The above example will return the next Downtimes between `2016-02-16` and `2016-02-22`

### Response

```json
[
	{
		"account_id": 122,
		"created_at": "2016-02-16T12:55:19.072Z",
		"creator_id": 450,
		"deleted": false,
		"details": "Christmas Eve",
		"downtime_type_id": 444,
		"end_time": 1440,
		"from": "2016-12-25",
		"id": 3534,
		"leave": null,
		"resource_ids": {
			"0": "1386"
		},
		"start_time": 0,
		"state": "Approved",
		"timezone": null,
		"to": "2016-12-25",
		"updated_at": "2016-02-16T12:55:19.072Z",
	}
]
```
## Get a Specific Downtime


## Create a Downtime

* `POST /v1/:subdomain/downtimes` will create a new Downtime from the parameters passed.

### Response

```json
[
	{
		"account_id": 122,
		"created_at": "2016-02-16T12:55:19.072Z",
		"creator_id": 450,
		"deleted": false,
		"details": "Christmas Eve",
		"downtime_type_id": 444,
		"end_time": 1440,
		"from": "2016-12-25",
		"id": 3534,
		"leave": null,
		"resource_ids": {
			"0": "1386"
		},
		"start_time": 0,
		"state": "Approved",
		"timezone": null,
		"to": "2016-12-25",
		"updated_at": "2016-02-16T12:55:19.072Z",
	}
]

```
Key | Type | Description
--- | --- | --- | ---
resource_ids| array of intergers | The resource ids of the resources
creator_id | integer | Unique identifier of the Creator this Downtime is for. (Can be `null`)
from | string | Set a start_date for a range Time Offs
end | string | Set an end_date for a range of Time Offs
start_time | integer | Start time in minutes from midnight for this Downtime Duration (Can't be null)
end_time | integer | End time in minutes from midnight for this Downtime Duration (Can't be null)
details | string | Optional plain text details for the dowtime.
downtime_type_id | integer | Unique identifier of the Downtime Type this Downtime is for. (Can be `null`)


## Update a Downtime
* `PUT /v1/:subdomain/downtimes/5` will update the Downtime from the parameters passed and return
the JSON representation of the updated Downtime. If the user does not have access to update
the Downtime, you'll see `403 Forbidden`.


## Delete a Downtime

* `DELETE /v1/:subdomain/downtimes/5` will delete the Downtime specified and return `204 No Content`
if that was successful. If the user does not have access to delete the Downtime, you'll see `403 Forbidden`.


## Get Downtime Types

* `GET /v1/:subdomain/downtime_types` returns an `Array` of **Downtimes**.

### Default Downtime response

```json
[
	{
	  "id":1555,
	  "name":"Compassionate leave",
	  "account_id":348,
	  "created_at":"2016-02-02T11:17:45.000Z",
	  "updated_at":"2016-02-02T11:17:45.000Z",
	  "default":true
	}
]

