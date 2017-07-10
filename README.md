# containerized-database-schema-migrations
This is a proof of concept repo for doing postgresql database schema migrations with FlywayDB in a container as part of a Jenkins CICD pipeline.

## Why bother orchestrating database schema migrations?
- Your code is revisioned, your infrastructure (hopefully) is revisioned; your database updates should be revisioned!
- Application restarts shouldn't modify your database. Table level locks can be detrimental and should be avoided or scheduled.
- Your database changes should be repeatable
- Your database schema should be reproduceable
- Your database changes should be repeatable

## Why containerize them?
- Containers are awesome! You can run them anywhere.
  - That means developers can run them locally.
  - You can have your CICD pipeline run them.
- Hassle-free to run a change.
- You don't need to worry about correct JDK / JRE / other environments

## What is Flyway?
[FlywayDB](https://flywaydb.org/) is a Java application that will maintain the versioning of your database. All you need to do is provide it a directory of your changes, and name your sql files appropriately. Flyway will handle the rest. The best part is that the managed code is a domain specific language for your database (probs SQL).

## How do I run this demo?
1. Start the postgres database container
    ```
    docker-compose up -d db
    ```
1. Once confirmed it's running, check the migration status
    ```
    docker-compose run --rm flyway-info
    ```
1. Run an actual migration
    ```
    docker-compose run --rm flyway-migrate
    ```
1. Check to see the migration is listed in the Flyway info call
    ```
    docker-compose run --rm flyway-info
    ```
1. Cleanup
    ```
    docker-compose stop; docker-compose down --volumes
    ```
## Jenkins
You can run the provided Jenkins file as your CICD pipeline for your database.
