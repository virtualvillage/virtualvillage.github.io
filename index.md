---
layout: default
---

# Virtual Village

Virtual Village is open source micro-services for creating new
socially-aware applications. Socially-aware apps create online communities (i.e. virtual villages) which allow users to connect and share with each other.

Virtual village provides social-awareness features as a service,
so you can spend more time building the features that make your app unique. We provide backend  services which can be easily hosted in the cloud (AWS initially and later Google) that are extensible so you can tweak them to your liking.

# How it works


Villages can be statically defined by your application or your application can let its users
create their own private villages for their own use. You could configure a village to be "public" so any of your app users can participate in a village, or you can configure villages so they are visible to invitation-only members.   

When you "invite" someone to join a village, they get a notification letting them know you want them to join your village. Once they become a village member, they can see anything you share with that village (if you enabled permissions to do so), including all information you shared with that village before you added them. Managing invitations and village memberships are just some of the administrative features
included.

You can see the villagers in your village via the village directory feature, including their profile information they have permitted people to see.

The people and data you add to the village are normally visible by all villagers by default, but you can further restrict it depending on your settings.



# Concepts

A virtual village is similar to a social network. Your app can define a fixed village for all its users, or your app allow your users to create their own private villages. For example, an app can create a fixed village for all its users such as a "San Diego Musicians" application. An app could also allow its users to create their own private villages and invite their friends to join it, such as say an app that is for sharing information with just your neighborhood or apartment building.  

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
- We hope to see an ecosystem of Optional and 3rd party services made by others
  - e.g. Village Neighborhood watch service
  - e.g. Village photo book service
  - e.g. Village yelp-like review service
  - e.g. Village service provider directory (e.g. local taxis, house cleaning, etc.)
  - e.g. Village ride-sharing / car pool service
  - e.g. Village group purchasing service (e.g. Costco bulk buy and split-up)

# Examples of Applications you can build with Virtual Village

Below are just some examples that show how a few mobile apps leveraged Virtual Village services
to implement most or all of their app's features.

## Avino Apartments

Avino, a large apartment complex has built a simple mobile app for its residents.
Tenants can download the app and use it to interact with their apartment complex community.

To build this app, the app defined a fixed village named "Avino Apartments".
The app includes message boards for residents and apartment managers to post on.
The topics for message boards are fixed for this app and includes topics such as
"For Sale", "Community Events", "Welcome Wagon", and so on. The app uses file sharing to include
upload PDF files for apartment policies and rules, information about the pool and clubhouse
use, etc. The shared calendar is used for any complex events (e.g. when the parking lot is
  being repaved, or tenant appreciation party at the clubhouse).
A directory feature allows tenants to see the other tenants in the complex, and
if the tenant has enabled it, the ability for tenants to send them messages.

As tenants move into the complex, Avino uses their application to invite the
new residents to join. Residents can opt to show their profile name, avatar,
unit number, etc. with the village's directory feature.

All the above features can be built using just base the virtual village services
out of the box.

## Kid Sports

The Kid Sports app provides information and some community for sports teams (e.g.
  baseball, soccer, football, etc.) for youth sports teams.

A team (typically the coach) downloads the app and creates a Kid Sports "team" (aka a virtual village) for their sports team and creates a name and avatar for it. (e.g. Mills High School Cougars Football). The couch notifies the players and/or their parents via the invitation
feature to join the
Kid Sports village.

Kid Sports app uses virtual village base features for the following:
* Shared calendar for the team practices and games
* Uploaded PDF files for basic team information (e.g. required sports gear players need)
* Directory shows list of all players and coaches on team
* villager-to-villager messages for communications between coach, players and parents.
* message boards for coach to post information for players and parents to read
* Each player uploads and shares their I.C.E. (In Case of Emergency) PDF form via file sharing

Kid Sports used the data model extension capability to put some app-specific information such as:
- additional fields added to profile to include player jersey number, position, player stats, etc.
- additional fields were added to profile for coaches to describe what coaching role they have

The extensions required no changes to services code, the system backend supports the app
with no modifications other than additional fields were defined in the metadata entity.

With virtually no work, coaches can now organize their teams easier and communicate with
players and their parents more easily. The I.C.E. forms are very useful for health and safety
should a kid get hurt during practice or a game when parents are not around, which is something few sports teams have on
hand in case of emergencies. A virtual village maps to a sports team in a natural way.

## Shared Buyer

Shared Buyer is an app created for people (family, friends and neighbors) to
pool their resources to purchase items at the store in bulk quantities (usually food) to get
more for less money. For example, a few neighbors can go in on buying bulk hamburger at Costco
and split up the purchase between them.

Shared Buyer allows users to create their own virtual villages (called "Purchasing Clubs" in this app) so they can create a private network of friends that want to participate in group purchases.

The shared calendar is used to plan which stores and which days shopping will occur.
The group message board is used for threaded discussions on what things the club wants to buy.
The villager-to-villager messaging is used for coordination communications.

This app creates its own shopper service for purchases, where club members (villagers)
can state which items they want and what fractional quantity they want to get out of the
bulk item (e.g. how many pounds of hamburger). This shopper
service also is used to enter the actual item and price paid w/ tax. The shopper service helps
assign how much each person owes for the item who is in the group purchase.

Except for the shopper services which is unique for this app, virtual village provides the
all the backend features this app requires. Virtual villages are mapped in a natural way to
purchasing clubs.

## Helpies

Helpies is an app which allows people to create their own private networks for asking
for volunteer assistance from others. Helpies can be used to get help from a village of your friends and family for
personal assistance (e.g. I need help moving this weekend, I need someone to feed my dog while
  I'm away on vacation, etc. ). Helpies could even be used for work, for example creating a
  village for an organization or sub-organization that helpies can be posted to (e.g. I need someone to help me
    compile a list of top customers, I need help fixing this tricky bug, etc.).

Although people can email (or text) people for help, having a village that collectively
can be notified of things people need help with and can volunteer for them is useful.
Helpies also tracks who is helping and has simple award badges that show up with villager
profile information in the village Directory.

In many ways, Helpies are entered and tracked like tickets in a bug tracking system or CRM issue tracking system, but instead of these being assigned they are made available for others in the
village to volunteer to help resolve them.

Helpies can be created with Virtual Village base for most of its features. The only modification is to populate the
the profile extension with badge/award fields. There is also an app-specific service required
called Helpies Service for managing and querying for Helpies. At the end, Helpies decided to
make their Helpie service available for others to use in their own apps. The
"Church App" who's users create villages for their own church, reused Helpies service to help orchestrate their church members to better help each other.


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

We use **PostgreSQL** as our database, which you can host yourself on your development
machine and is also available as hosted service in most public cloud platforms.

Most of the data in the database is scoped (or qualified) by the village
it belongs to. The data is meant to be visible only by the village it is scoped to.
For example, invitations or villager messages are scoped to the village they
are used for and other villages can not see invitations or messages that belong to
a different village.

A single app can define and use as many villages
as you want, and the domain model allows even villagers to create their own villages.

Note that a user can be a member of one or many villages. Your app can define a fixed village
for all its users. Your app could also enable users to create their own private villages and invite users to join them. Both methods of using villages are supported.

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
