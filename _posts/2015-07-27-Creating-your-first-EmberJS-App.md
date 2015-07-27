---
layout: post
title: "Creating your first Ember JS app w/ Apitools."
quote: "Ember-cli + Apitools == Instant App."
image: true
video: false
comments: true
---

A couple of [http://www.meetup.com/Ember-js-Barcelona/events/223198909/](weeks ago) we reloaded the local [http://emberjs.com/](EmberJS) Barcelona meetup. 

For the occasion I wrote a quick application to show everyone how easy it easy to start developing with EmberJS. 
The idea was to recreate the feeling that first time Rails devs get when they start scaffolding. They type a few commands and everything works out of the box.

I also wanted to take the opportunity to stress the importance of thinking in terms of mircoapps for development agility and quick prototyping.

A microapp A microapp is small, self-contained, application focused on doing one thing and doing it well. Microapps can be integrated into more complex projects and use language agnostic APIs to communicate. Microapps speed up prototyping, innovation and therefore adoption of new technologies.

I decided to show off EmberJS capabilities with an app retrieving and displaying public Github events.

Not to get involved w any backend development I decided to use [https://www.apitools.com/](Apitools) as middleware between my EmberJS app and Github API.

[Ember-GithubAPI-Apitools](https://raw.githubusercontent.com/nopressurelabs/blog/gh-pages/assets/images/ember-apitools.png "Ember - Apitools - Github API")

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
    
Setting up [https://www.apitools.com/](Apitools) is almost instant. We just [https://www.apitools.com/accounts/sign_in](sign in), and create a service by using the Github premade example. 

Once the service is setup on Apitools, we integrate this in our Routes in our EmberJS app.
Routes in Ember are sometimes a complicated concept, especially if you come from Rails.

More specifically:
- Routes represent application URLs
- Routes represent RESTful resources
- Routes represent app states

We siply have to add an index.js route to pull events from Apitools.
    
    # app/routes/index.js

    import Ember from "ember";

    var IndexRoute = Ember.Route.extend({
      model: function(params) {
        return Ember.$.getJSON(
            "https://github7ad43e39-bd5086abac4b.my.apitools.com/events?per_page=" 
            + params.per_page);
      }
    });
    
    export default IndexRoute;
        

We will then add a template to display the data we pull from the Github APIs.
Ember.js uses the [http://handlebarsjs.com/](Handlebars) templating library to power your app's user interface. Handlebars templates are just like regular HTML, but also give you the ability to embed expressions that change what is displayed.

    
    # app/templates/index.hbs
    
    {{#each event in model}}
        <li>
          <div>
            <strong>Github Event:</strong>
            <p>id: {{event.id}}</p>
            <p>type: {{event.type}}</p>
            <p>github user: </p>
            <p>
              <a {{bindAttr href=event.actor.url}}>
                <img style="width: 40px" {{bindAttr src=event.actor.avatar_url}}> 
                {{event.actor.login}}
              </a>
            </p>
            <p>github repo: </p>
            <p>
              <a {{bindAttr href=event.repo.url}}>
                {{event.repo.name}}
              </a>
            </p>
          </div>
        </li>
    {{/each}}
    
And that's it! You have your EmberJS microapp and can start visualising APIs traffic on [https://www.apitools.com/](Apitools).

Repo for microgit is availiable on [https://github.com/nopressurelabs/Microgit](Github).

If you are interested in microapps development and developing APIs w/ Rails you can checkout my book: [http://shop.oreilly.com/product/0636920034469.do](RESTful Rails Development).

If you want to find out more about all you can do with [https://www.apitools.com/](Apitools) check [https://www.apitools.com/](apitools.com).
