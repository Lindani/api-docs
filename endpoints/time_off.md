# Time Off

## Get Time Off/Downtime Events

* `GET /v1/:subdomain/downtimes` returns an `Array` of **Time Off/Downtime events**.

### Query String Parameters

Parameter | Default | Description
--- | --- | --- | ---
resource_ids | | Only retrieve Time Off/Downtime events for the given resources 
limit | 50 | Limit the number of results returned for pagination. To retrieve all the results use `0`.
offset | 0 | Offset the results for pagination, starting from the given record number.
from | | Set a start date range for Time Off/Downtime events.
to | | Set an end date range for Time Off/Downtime events.

**Example:**

```
https://api.resourceguruapp.com/v1/example-corp/downtimes?resource_ids[]=123&resource_ids[]=122&from=2016-02-16&to=2016-02-22
```
The above example will return the next Time Off/Downtime events between `2016-02-16` and `2016-02-22` where the resource ids are 123 and 122.

### Response

```json
[
	{
		"account_id": 1,
		"created_at": "2016-02-16T12:55:19.072Z",
		"creator_id": 2,
		"deleted": false,
		"details": "Christmas Eve",
		"downtime_type_id": 3,
		"end_time": 1440,
		"from": "2016-12-25",
		"id": 123,
		"leave": null,
		"resource_ids": {
			"0": "123"
		},
		"start_time": 0,
		"state": "Approved",
		"timezone": null,
		"to": "2016-12-25",
		"updated_at": "2016-02-16T12:55:19.072Z",
	},
	{
		"account_id": 1,		
		"created_at": "2016-02-04T09:48:24.000Z",
		"creator_id": 2,		
		"deleted": false,		
		"details": "Details",		
		"downtime_type_id": null,		
		"end_time": 1440,		
		"from": "2016-02-22",		
		"id": 124,		
		"leave": null,		
		"resource_ids": {
			"0": 123
		},
		"start_time": 0,		
		"state": "Approved",		
		"timezone": null,	
		"to": "2016-02-22",	
		"updated_at": "2016-02-12T11:46:54.000Z"
	}

	{
		"account_id": 1,		
		"created_at": "2015-12-17T13:00:40.000Z",		
		"creator_id": 2,		
		"deleted": false,		
		"details": "",		
		"downtime_type_id": null,		
		"end_time": 1440,		
		"from": "2016-02-22",		
		"id": 125,		
		"leave": null,		
		"resource_ids": {
			"0": 122
		},
		"start_time": 0,		
		"state": "Approved",		
		"timezone": null,	
		"to": "2016-02-22",	
		"updated_at": "2015-12-17T13:02:01.000Z,	
	}
]
```

Key | Type | Description
--- | --- | ---
created_at | string | Time Off/Downtime event creation date and time.
creator_id | integer | Unique identifier of the User this Time Off/Downtime event was created by.
deleted | boolean | Denoted whether the Time Off/Downtime event has been deleted.
details | string | Extra details about this Time Off/Downtime event.
downtime_type_id | integer | Unique identifier of the Time Off/Downtime event Type this Time Off/Downtime event is for. (Can be `null`)
end_time | integer | End time in minutes from midnight for this Time Off/Downtime event duration (Can't be null)
from | string | Start date for the Time Off/Downtime event.
id | integer | Unique identifier for a Time Off/Downtime event.
resource_ids| array of intergers | Unique identifiers of the Resources this Time Off/Downtime event is for.
start_time | integer | Start time in minutes from midnight for this Time Off/Downtime event duration (Can't be null)
state | string | Status details about the Time Off/Downtime event.
timezone | string | Specified time zone for the Time Off/Downtime event.
to | string | End date for the Time Off/Downtime event.
updated_at | String | Last updated date and time.


## Get a Specific Time Off/Downtime Event

*  `GET /v1/:subdomain/downtimes/id` returns a specific Time Off/Downtime Event.

## Create a Time Off/Downtime Event

* `POST /v1/:subdomain/downtimes` will create a new Time Off/Downtime event from the parameters passed.

### Response

```json
[
	{
		"account_id": 1,
		"created_at": "2016-02-16T12:55:19.072Z",
		"creator_id": 2,
		"deleted": false,
		"details": "Christmas Eve",
		"downtime_type_id": 444,
		"end_time": 1440,
		"from": "2016-12-25",
		"id": 123,
		"leave": null,
		"resource_ids": {
			"0": "122"
		},
		"start_time": 0,
		"state": "Approved",
		"timezone": "London",
		"to": "2016-12-25",
		"updated_at": "2016-02-16T12:55:19.072Z",
	}
]

```
Key | Type | Description
--- | --- | --- | ---
resource_ids| array of intergers | The resources that the Time Off/Downtime event is being created for.
creator_id | integer | Unique identifier of the User this Time Off/Downtime event is for.
from | string | The ISO 8601 formatted first date for the Time Off/Downtime event.
to | string | The ISO 8601 formatted last date for the Time Off/Downtime event.
start_time | integer | Start time in minutes from midnight for this Time Off/Downtime event duration (Can't be null)
end_time | integer | End time in minutes from midnight for this Time Off/Downtime event duration (Can't be null)
details | string | Optional plain text details for the Time Off/Downtime event.
downtime_type_id | integer | Unique identifier of the Time Off/Downtime event Type this Time Off/Downtime event is for. (Can be `null`)
timezone | string | String denoting the time zone for which the Time Off/Downtime event is created for. [(Details)](#time-zones)

#### Time zones

When creating a new Time Off/Downtime event, a time zone may be specified if the Time Off/Downtime event is being created for multiple resources. If left blank, it will default to the time zone of each resource.
The time zone values are based off of Ruby On Rails's ActiveSupport::TimeZone's key mappings. For example, to create a Time Off/Downtime event for (GMT +0) London, the value would be "London". See http://api.rubyonrails.org/classes/ActiveSupport/TimeZone.html - Constants.


## Update a Time Off/Downtime Event
* `PUT /v1/:subdomain/downtimes/5` will update the Time Off/Downtime event from the parameters passed and return
the JSON representation of the updated Time Off/Downtime event. If the user does not have access to update
the Time Off/Downtime event, you'll see `403 Forbidden`.


## Delete a Time Off/Downtime Event

* `DELETE /v1/:subdomain/downtimes/5` will delete the Time Off/Downtime event specified and return `204 No Content`
if that was successful. If the user does not have access to delete the Time Off/Downtime event, you'll see `403 Forbidden`.


## Get Time Off/Downtime Event Types

* `GET /v1/:subdomain/downtime_types` returns an `Array` of **Time Off/Downtime events**.

```json
[
	{
	  "id": 1555,
	  "name": "Compassionate leave",
	  "account_id": 348,
	  "created_at": "2016-02-02T11:17:45.000Z",
	  "updated_at": "2016-02-02T11:17:45.000Z",
	  "default": true
	}
]

```
Key | Type | Description
--- | --- | --- | ---
id | integer | Unique identifier of the Time Off/Downtime event type.
name | string | Name of this Time Off/Downtime event type.
account_id | integer | Unique identifier of the Account to which this Time Off/Downtime event type belongs.
created_at | string | Time Off/Downtime event type creation date and time.
updated_at | string | Last updated date and time.
default | boolean | Denotes whether the Time Off/Downtime event type is a default type.
