
## Database Design

The database schema is simple and all tables have an optional JSON field for
adding your own app-specific data to them. We use stored procedures to optimize database performance and to make it easier to modify or extend database schemas without breaking your code. We put zero "business logic" in stored procedures, they may only include data integrity, validation or basic SQL Query and CRUD capability. We designed the schema to be as simple as possible so it's easy to understand, debug or extend if need be. We chose PostgreSQL for it's features, ease of use, referential integrity / join capability, performance and its operational (e.g. backup/restore, replication, etc.) capabilities. Your app's service can choose to use PostgreSQL or you can use other databases (e.g. A NoSQL database). There is no requirement that you use the Virtual Village database for your services.

Our database is currently designed for single-app-tenancy only.
Each "app" you build should
 run on a separate database instance.

We'd like to say that you won't need to know anything about PostgreSQL, but that wouldn't be realistic. You should have some basic SQL and operational knowledge of the database.

Our domain model is composed of the following entities:

| Entity       | Description                                                     |
|:-------------|:----------------------------------------------------------------|
| Villages     | Definitions of the villages your app uses                       |
| Users        | User and user/profile information, not specific to any village  |
| Memberships  | Links Users to Villages, also includes membership attributes    |
| Invitations  | Village Invitations to join a village sent to persons           |
| Messages     | Villager to villager messages                                   |
| Topics       | Village Topic / group message boards                            |
| Calendar     | Village shareable calendar events                               |
| Files        | Village shareable file references (physical file stored in S3)  |
| Metadata     | Metadata JSON documents for extensibility and configuration     |

Return to [Home](../index.md).
