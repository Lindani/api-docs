# Time Off

## Get Downtimes

### Query String Parameters



## Get a Specific Downtime

## Create a Downtime

* `POST /v1/:subdomain/downtimes` will create a new Downtime from the parameters passed.

### Response

```json
[
	{
		"account_id": 122,
		"created_at": "2016-02-16T12:55:19.072Z",
		"creator_id": 146,
		"deleted": false,
		"details": "Christmas Eve",
		"downtime_type_id": 1137,
		"end_time": 1440,
		"from": "2016-12-25",
		"id": 1871,
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
resource_ids[]| array of intergers | The resource ids of the resources
creator_id | | 
from | string | Set a start_date for a range Time Offs
end | string | Set an end_date for a range of Time Offs
start_time | integer | Start time in minutes from midnight for this Downtime Duration
end_time | integer | End time in minutes from midnight for this Downtime Duration
details | string | 
downtime_type_id | integer | 



## Update a Downtime
## Delete a Downtime

## Get Downtime Types