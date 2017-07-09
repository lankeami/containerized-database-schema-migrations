# containerized-database-schema-migrations
Proof of concept repo for doing database schema migrations with FlywayDB

## Why bother orchestrating database schema migrations?
- Your code is revisioned, your infrastructure (hopefully) is revisioned; your database updates should be revisioned!
- Your database changes should be repeatable
- Your database schema should be reproduceable
- Your database changes should be repeatable

## Why containerize them?
Containers are awesome! You can run them anywhere. That means developers can run them locally or you can have your CICD pipeline run them. Containerizing your database migration service means it's hassle-free to run a change in your development environment or in your QA environment or even in your production environment.

## What is Flyway?
[FlywayDB](https://flywaydb.org/) is a Java application that will maintain the versioning of your database. All you need to do is provide it a directory of your changes, and name your sql files appropriately. Flyway will handle the rest.

## How do I run this demo?

