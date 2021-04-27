These are my follow along notes for [The Complete React on Rails Course](https://learnetto.com/users/hrishio/courses/react-rails-course).

Here are the steps I took:

* At the command line:
  ```
  rails new eventlite --webpack=react
  cd eventlite
  ```
* created [index.html.erb](app/views/events/index.html.erb)
* created the [events controller](app/controllers/events_controller.rb)
* updated [routes.rb](config/routes.rb)
* started the server

This yields the error **Webpacker::Manifest::MissingEntryError in Events#index**, with the additional explanatory text:

```
Webpacker can't find hello_react in /Users/sam/source-control/learnetto-react-rails/eventlite/public/packs/manifest.json. Possible causes:
1. You want to set webpacker.yml value of compile to true for your environment
   unless you are using the `webpack -w` or the webpack-dev-server.
2. webpack has not yet re-run to reflect updates.
3. You have misconfigured Webpacker's config/webpacker.yml file.
4. Your webpack configuration is not creating a manifest.
Your manifest contains:
{
}
```

At this point, I started reading some of the existing discussions, and ran the following commands based on your advice to another reader:

* ran `bundle exec rails webpacker:install`.  This led to conflicts in `config/webpacker.yml` and `babel.config.js`, both of which I allowed the script to overwrite.
* ran `bundle exec rails webpacker:install:react`. 

Unfortunately, this led to the same error as before. 

(Also re-ran `yarn`, which didn't change anything.)