# Should Server machines holds the Databases as well?
> No databases and application code should not reside in same machine. Because ->
> 1. Both application and database will gets tightly coupled , failure in machine will affect both db and server code.
> 2. Becuase of tight coupling , adding/ removing of any app/db will have to add both app and db.
> 3. Sharding of data in db will not be possible
> 4. Fewer resources are available for the code since the database will also use some of the resources in the machine.
