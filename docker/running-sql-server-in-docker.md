# Running SQL Server in Docker
To easily setup and restore databases for a developer, it might be very nice to have the database (or other components) in Docker. MS has a docker image for sql server, it runs on linux.

## Restoring a backup into a docker container
This [article](https://docs.microsoft.com/en-us/sql/linux/tutorial-restore-backup-in-sql-server-container?view=sql-server-ver15) shows how to create a new container from a MS image for sql server 2019 and how to restore an existing backup into it.

# Todo
* [x] Find out how to restore a backup into docker
* [ ] Test restoring an encrypted backup into docker