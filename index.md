---
layout: default
---

# What it's for

Virtual village is for creating new applications which can leverage a "virtual village"
for socially-aware applications.

# Concepts

A virtual village is similar to a social network. Your app can define a fixed village for all its users, or your app allow your users to create their own private villages. For example, an app can create a fixed village for all its users such as a "San Diego Musicians" application. An app could also allow its users to create their own private villages and invite only their friends to it, such as say an app that is for sharing information with just your neighborhood or apartment building.  

# Platform Features
* * *
### Villages
- create fixed village(s) for all app users
- ability for users to create their own villages

### Village invitations
- users create and manage invitations to their villages
  - email
  - manually add / remove users
- email sending of village invitations for new users
- invitation response handling and management

### Users
- user management for your app
- user profiles (photo/avatar, name, contact info, etc.)
- user-selectable profile sharing options

### Village Directory
- list all villagers and their profiles
- options for shared profile in

### Villager Communications    
- one-to-one villager messaging
- broadcast messages for all villagers
- message boards w/ threaded discussion
  - fixed topics
  - user-defined topics

### Village memberships
- Village-level permissions roles (admin, user, etc.)
- Supports app-defined roles (e.g. MESSAGE_BOARD_POSTER, HELPER, etc.)

### File sharing
- Upload/download files into S3
- Share settings (all villagers, specific villagers, private)

### User Notifications
- Mobile Push notifications
- Email Notifications
- Web socket notifications

# Design Philosophy

We like a micro-services library approach to building applications. The idea is that
you can use our micro-services as-is for basic social-awareness features, but the
bulk of your app will be built and run independently with the technology you prefer.
This is unlike "platform" or "framework" types of design. We presume you want social-awareness
and our related features available as services, as opposed to foisting our technology or
code base upon you.

Virtual Village is not meant to be a comprehensive platform for your app, but rather
it creates an extensible set of micro-services that your app can leverage for it's backend.
In this way, it's more of a starter kit of micro-services to implement commonly used (boilerplate)
core services so you can focus your time and energy on the secret sauce that makes your app unique.

Although our implementation uses a Go-based technology stack, you can add on to the
backend with micro-services of your own design using the technology stack you prefer,
for example with Node.js or Lambda functions.  

There are a few "extension points" which may require you to work with our Go technology stack,
but the majority of your app should work using Virtual Village as just a suite of stand-alone
services.

We allow you to have access to source to modify it to your liking. Once we get enough
users to warrant it we may one day consider offering these services hosted for you to make
it even easier. 


# Architecture Principles
 Go, Postgres, etc.


Text can be **bold**, _italic_, or ~~strikethrough~~.

[Link to another page](another-page).

There should be whitespace between paragraphs.

There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.

# [](#header-1)Header 1

# headerme too

This is a normal paragraph following a header. GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.

## [](#header-2)Header 2

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### [](#header-3)Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### [](#header-4)Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### [](#header-5)Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### [](#header-6)Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![](https://assets-cdn.github.com/images/icons/emoji/octocat.png)

### Large image

![](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
