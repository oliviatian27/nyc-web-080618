# Rails Review Donut Shoppe

- Create our donuts: `rails g resource Donut name sprinkles:boolean filling tasty:boolean`

  - `resource` gives us: a migration, a model, a controller, RESTful routes, and an empty views folder

- We could also accomplish this with:
  - `rails g controller Donuts`. This will give us an empty views folder and a `DonutsController`
  - `rails g model Donut name sprinkles:boolean filling:string tasty:boolean`. This will create a migration and a model
    for us.
  - We'd then have to manually add the RESTful routes to `config/routes.rb`

---

### Routes.rb:

```ruby
Rails.application.routes.draw do
  # when I receive a GET request to /donuts/new, CALL DonutsController#new. ALSO, create a helper method called new_donut_path
  get '/donuts/:id', to: 'donuts#show', as: 'donut'
  delete '/donuts/:id', to: 'donuts#destroy', as: 'destroy_donut'
  get '/donuts/new', to: 'donuts#new', as: 'new_donut'
  get '/profile', to: 'donuts#profile'
  # get('/donuts/new', { to: 'donuts#new', as: 'new_donut' })
end
```

- All of the above can be abbreviated (except for the `/profile` route) by using `resources`:

```ruby
  resources(:donuts, { only: [:show, :new, :destroy] })
```

### MVC Architecture:

![](https://github.com/learn-co-students/nyc-web-080618/raw/master/18-REST-review-donut-shoppe/mvc_request.jpg)

---

### Mapping HTTP Verbs to CRUD and SQL:

![](https://github.com/learn-co-students/nyc-web-080618/raw/master/18-REST-review-donut-shoppe/http_crud.jpg)

---

### RESTful Routes:

![](https://github.com/learn-co-students/nyc-web-080618/raw/master/18-REST-review-donut-shoppe/RESTful_routes.png)

---

### External Resources:

- [Rails Docs on Generators](https://guides.rubyonrails.org/command_line.html#rails-generate)
- [Rails Docs on Routing](https://guides.rubyonrails.org/routing.html#resource-routing-the-rails-default)
- [Restular](http://www.restular.com/)
