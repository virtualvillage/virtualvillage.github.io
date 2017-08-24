---
layout: default
---

# Virtual Village

Virtual Village is open source micro-services for creating new
socially-aware applications. Socially-aware apps to create online communities (i.e. virtual villages) which allow users to connect and share with each other.

Virtual village provides some basic social-awareness features
common to many socially-aware apps off the shelf for you to use,
so you can spend more time building the features that make your app unique. We provide backend core services which can be hosted in the cloud (AWS initially and later Google) that are extensible so you can tweak them to your liking.

# What it's for

You can use virtual villages to control who you share with. Add people to a village, then share with that circle so village members (aka villagers) can see it. Virtual villages includes some basic
features useful to most any socially-aware application
out of the box such as villager communications, message boards, files, notifications, etc. But the real value of a village comes with the shared features or information unique to your app.

Villages can be statically defined by your application, or your application can let its users
create private villages for their own use. You could configure a village to be "public" so any of your app users can participate in a village, or you can configure villages so they are visible to invitation-only members.   

When you "invite" someone to join a village, they might get a notification letting them know you added them to one of your villages. They can see anything you share with that village (if you enabled permissions to do so), including information you shared with that village including that before you added them. Managing invitations and village memberships are just some of the adminstrative features
included by the services.

You can see villagers you have in your village via the village directory features, including their profile information they have permitted people to see.

The people and content you add are normally publicly visible by default to all villagers, but you can change who can see or modify information depending on your settings.



# Concepts

A virtual village is similar to a social network. Your app can define a fixed village for all its users, or your app allow your users to create their own private villages. For example, an app can create a fixed village for all its users such as a "San Diego Musicians" application. An app could also allow its users to create their own private villages and invite only their friends to it, such as say an app that is for sharing information with just your neighborhood or apartment building.  

# Virtual Village Features
* * *

### General
- Requires use of Village, Memberships and User services, the rest is optional
- REST Services
- Web socket API for real-time updates
- Mobile PUSH notification integration
- Optional client SDK's (Swift, Javascript, Java)
  - Realm database integration for mobile SDK
- JWT tokens between client-server communications

### Villages
- Create fixed village(s) for all app users
- Allow your users to create and manage their own private villages

- Village visibility options
  - public - anyone can view the village and contents
  - private - only village members can view village and contents

### Village memberships (aka villagers)
- Can manually add / remove users from village
- Village-level permission roles (admin, user, etc.)
  - Supports app-defined roles (e.g. MESSAGE_BOARD_POSTER, HELPER, etc.)


### Village invitations
- Create and manage invitations to join villages
  - Email delivery of village invitations to non-users
- Email delivery of village invitations for new users
  - Email content configurable by app
- Invitation response handling and management


### User management
- Sign up
- Sign on / Log out
- User profiles and preferences (photo/avatar, name, contact info, etc.)
  - Villager-tunable profile sharing options
  - Option to add I.C.E. (In Case of Emergency) info to a profile
- Profile and preference data can be extended by app
- Future: Auth0 and other auth integration options

### Village Directory
- list and manage all villagers and their profiles
  - options for sharing profile info with village
- Ability to add non-users to a directory (e.g. a doctor or a school)

### Village calendar
- View and manage calendar events

### Village Communications    
- Villager-to-villager messaging
- Broadcast messages for all villagers
- Topic message boards w/ threaded discussion
  - App-defined fixed topics
  - Support for villager-defined topics

### Configuration
- Ability to modify hosts, database configurations, etc. easily in "10 factor" manner.
- Metadata for extensibility stored in PostgreSQL for metadata-driven capabilities

### Village file sharing
- Upload/download files into S3 for sharing
  - File sharing village permissions for file show/hide, read/write, etc.


### Village Streams
- Service data updates get published to message stream so your app can react to changes
  - Configure events for PUSH notifications and web services API


### Add-on Village Services
- Ecosystem of Optional and 3rd party services made by others
  - e.g. Village Neighborhood watch service
  - e.g. Village photo book service
  - e.g. Village yelp-like review service
  - e.g. Village service provider directory (e.g. local taxis, house cleaning, etc.)
  - e.g. Village ride-sharing / car pool service
  - e.g. Village group purchasing service (e.g. Costco bulk buy and split-up)


# Design Philosophy

We like a micro-services library approach to building applications. The idea is that
you can use our micro-services as-is for basic social-awareness features, but the
bulk of your app will be built and run independently using the technologies you prefer
for maximum flexibility.
This is unlike "platform" or "framework" types of approaches. We presume you want social-awareness
and our related features available as separate services, as opposed to foisting our technology stack and code base upon you.

Virtual Village is not meant to be a comprehensive platform for your app, but rather
it creates an extensible set of micro-services that your app can leverage for it's backend.
In this way, it's more of a starter kit of micro-services to implement commonly used (boilerplate)
core services so you can focus your time and energy on the secret sauce that makes your app unique.

Although our implementation uses a Go-based technology stack, you can add on to the
backend with micro-services of your own design using the technology stack you prefer,
for example with Node.js or Lambda functions.   

There are a few "extension points" which you may want you to work with our Go technology stack,
but these should be the exceptional case, not the norm. The majority of apps should work using Virtual Village as just a suite of stand-alone services.

We allow you to have access to source code so you can modify it to your liking if need be. If we get enough users that request it, we may one day consider offering these services hosted in the cloud for you to make it even easier to use them.


# Architecture

 ![](https://raw.githubusercontent.com/virtualvillage/virtualvillage.github.io/master/architecture.png)

## Cloud-friendly

The architecture is designed so services are straightforward to host in public or private clouds. The initial version will target AWS, but we hope to support Google cloud available shortly after.
The main cloud-specific components are services that have a reliance on cloud services (e.g. S3, Kinesis). We may opt to refactor for serverless cloud platforms, but at this time they are still cloud-dependent and primarily javascript/node.js oriented.

## Service implementation language

The services are built using **Go** language. We include docker setup for them, but this is optional.
We like Go's simplicity, performance and capabilities of its standard libraries. You won't need
to work in Go unless you want to modify/view a service's source code.  

## Docker

The services are designed to be used with Docker, but this is optional. You can deploy with or
without Docker.

## Database

We use **PostgreSQL** as our database, which you can host yourself or is available hosted in most cloud environments. The database schema is simple and all tables have an optional JSON field for
adding your own app-specific data to them. We use stored procedures to optimize database performance and to make it easier to modify or extend database schemas without breaking your code. We put zero "business logic" in stored procedures, they may only include data integrity, validation or basic SQL Query and CRUD capability. We designed the schema to be as simple as possible so it's easy to understand, debug or extend if need be. We chose PostgreSQL for it's features, referential integrity / join capability, performance and its operational (e.g. backup/restore) capabilities. Your app's service can choose to use PostgreSQL or you can use other databases (e.g. A NoSQL database). There is no requirement that you use the Virtual Village database for your services.

We'd like to say that you won't need to know anything about PostgreSQL, but that wouldn't be realistic. You should have some basic SQL and operational knowledge of the database.

Our schema is composed of the following entities:

| Table        | Description                                                     |
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

Our database is designed for single-app-tenancy only. Each "app" you build should
probably run on it's own database instance. A single app can define and use as many villages
as you want, even villager-created ones. Note that a user can be a member to many villages,
as this enables your users to create lots of private villages and other users can join them.
Most of the entities and features are village-scoped, that is the features (e.g. invitations
, village directory, message boards) are meant to apply to one and only one village.

You can easily extend our PostgreSQL schema by adding more tables to build out your own features
as you wish. This is probably the easiest way to add features, but by design you don't
have to build your features using PostgreSQL.

## Caching

We use **Redis** for our caching infrastructure. We will later support AWS and Google cache services as well. We store only in-memory data in Redis, we do not rely on it's persistence features.

## Eventing

We initially support **AWS Kinesis** and **Kafka** integration. We hope to add Google messaging support soon.


# Frequently Asked Questions

- Do you provide front-end components too?
  - We provide backend REST services and some optional client-side API's for using them (Swift, ES6 and Java). In the future, we may eventually provide some optional UI components.

- Do you have plans to offer Virtual Village as a hosted cloud service?
  - If we have enough interest, we may consider it. Since this implies SLA's, hosting costs, etc.
    it would be a kind of commercial product offering.

* * *
