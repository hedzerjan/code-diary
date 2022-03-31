# Hangfire behind MVC for scheduled actions
## Calling
It should be easy to call from a mediator command. Therefore a static bridge class with methods should suffice. The methods can then upon actual execution create new mediator commands. Why a new mediator command? It allows us to use pipelines to add behavior to the actual command.

The library that contains the bridge class should be accessible from both mvc and the hangfire server.

## Execution
Upon execution a new scope has to be created in order to have scoped services that use the correct tenant-connectionstring. It is ok for the logging to end up on the big pile, there has to be an audit trace.

### Followup actions
It might be nice to send e-mails out upon completion of the various tasks

## Todo
* [ ] Lookup followup actions
* [ ] Try to seperate ITenantRequest from ITenantJobRequest