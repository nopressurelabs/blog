---
layout: post
title: "Creating your first Ember JS app w/ Apitools."
quote: "Ember-cli + Apitools == Instant App."
image: true
video: false
comments: true
---

A couple of [http://www.meetup.com/Ember-js-Barcelona/events/223198909/](weeks ago) we reloaded the local EmberJS Barcelona meetup. 

For the occasion I wrote a quick application to show everyone how easy it easy to start developing with EmberJS. 
The idea was to recreate the feeling that first time Rails devs get when they start scaffolding. They type a few commands and everything works out of the box.

I also wanted to take the opportunity to stress the importance of thinking in terms of mircoapps for development agility and quick prototyping.

A microapp A microapp is small, self-contained, application focused on doing one thing and doing it well. Microapps can be integrated into more complex projects and use language agnostic APIs to communicate. Microapps speed up prototyping, innovation and therefore adoption of new technologies.

I decided to show off EmberJS capabilities with an app retrieving and displaying public Github events.

Not to get involved w any backend development I decided to use [https://www.apitools.com/](Apitools) as middleware between my EmberJS app and Github API.

Our microapp in EmberJS is called Microgit. Microgit can:

- Retrieve public Github events
- Use Apitools as middleware to talk to ext APIs
- Use EmberJS as frontend framework

To get started we first need to prepare our environment:
    
    $ npm install -g ember-cli 
    
    $ npm install -g bower
    
    $ brew install watchman
    
    $ npm install -g phantomjs
    
    $ ember new microgit
    

    




