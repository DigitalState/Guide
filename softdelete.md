# Soft-Delete

DigitalState microservice implement a "soft-delete" functionality which ensures that only users with the appropriate permissions can permanently purge data from a microservice's database.

With a few exceptions, whenever a DELETE method is actioned, a soft-delete occurs.

By default, all GET methods return non-deleted content even when not using the deleted=false query param.

## API Query Params for Soft Delete

Query Param: `deleted`

Possible values:

- `null`: (literal word) Returns all entities, whether they have been deleted or not.
- `false`: Returns entities that are not deleted.
- `true`: Returns entities that have been deleted.

See the DigitalState Postman Collection in the SDK Repo for further examples of the `deleted` query param.

## How to Un-Delete soft-deleted content?

...

## How does Soft-Delete work?

Each entity that has soft-delete enabled, implements a database column (COLUMN NAME GOES HERE), which tracks the timestamp of when that database record was deleted.

## What Happens when you Create new content?

...

## What happens when you delete content?

... something like timestamp is applied

## What happens when you un-delete content?

... something like the column value is returned to null? Is there a log or somesort of history of un-deletion?  If not, but its planned (not saying it is, just asking), then create a ticket and link to it.

## How to Permanently Delete data?

...
If there not currently a API for this then explain how a API function is not currently implemented.  Create a Ticket/issue for it, and Link to that ticket.


## Various Conditions

1. What happens when you GET/PATCH/PUT on a soft-deleted item? Do i have to apply the query param to access it?
1. Can i PATCH/PUT on a soft-deleted item? If not, what is required? aka: you must un-delete the item fist, aka soft-delete is a hardened snapshot in time.
1. Is there a data about who deleted it?
1. Is there data about who Un-deleted it?
1. Are there specific error messages about soft-deleted content?