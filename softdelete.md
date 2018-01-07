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

## How does Soft-Delete work?

Each entity that has soft-delete enabled, implements a property named `deletedAt`, which tracks the timestamp of when that database record was deleted.

## How to Un-Delete soft-deleted content?

In order to un-delete soft-deleted content, you will need to issue a PATCH request to the entity with `"deletedAt": null`.

## What Happens when you Create new content?

By default, when creating a new entity, the `deletedAt` column will be null. In other words, a non-deleted content.

## What happens when you delete content?

When issuing a DELETE request to an entity with soft-delete enabled, the row will remain in storage, however, the `deletedAt` property will be updated with the current timestamp. The entity will be then considered soft-deleted.

## How to Permanently Delete data?

Entities that has soft-delete enabled cannot be deleted outright from storage at the moment. See [ticket](https://github.com/DigitalState/Core/issues/33).

## Various Conditions

1. What happens when you issue a GET request on soft-deleted item(s)? Do i have to apply the query param to access it?
By default, only non-deleted items are returned. If the query param `deleted` is provided, then the expected behavior is as below:

- `null`: (literal word) Returns all entities, whether they have been deleted or not.
- `false`: Returns entities that are not deleted.
- `true`: Returns entities that have been deleted.

1. Can I PATCH/PUT on a soft-deleted item?
The item will get updated as normal. No additional parameters are needed.

1. Is there a data about who deleted it?
At the moment, there is no data about who deleted it.

1. Is there data about who Un-deleted it?
At the moment, there is no data about who un-deleted it.

1. Are there specific error messages about soft-deleted content?
At the moment, there are no specific error messages about soft-deleted content.
