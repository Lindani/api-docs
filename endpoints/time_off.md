# Time Off

## Get Downtimes

###Query String Parameters
### Query String Parameters

Parameter | Default | Description
--- | --- | --- | ---
 resource_ids| | | |
from | | Set a start_date for a range Time Offs
end | | Set an end_date for a range of Time Offs
start_time | | Set a start_time 
end_time | | Set an end_time


## Get a Specific Downtime

## Create a Downtime
**Example**

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

## Update a Downtime
## Delete a Downtime

## Get Downtime Types