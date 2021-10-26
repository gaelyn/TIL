[Rails Guides on Application Templates](https://guides.rubyonrails.org/rails_application_templates.html)

Application templates are Ruby files that can be included when making a new rails app and include DSL for adding gems, initializers, etc. to your app.

Example:
```ruby
gem_group :development, :test do gem 'rspec-rails'
  gem 'factory_bot_rails'
  gem 'capybara'
  gem 'webdrivers'
  gem 'faker'
end

initializer 'generators.rb', <<-CODE
  Rails.application.config.generators do |g|
    g.test_framework :rspec,
    fixtures:           false,
    view_specs:         false,
    helper_specs:       false,
    routing_specs:      false,
    request_specs:      false,
    controller_specs:   false
  end
CODE

after_bundle do
  generate 'rspec:install'
end
```
[Reference](https://www.codewithjason.com/complete-guide-to-rails-testing/)
1. The first chunk of code will add these gems to the Gemfile.
1. The second chunk of code creates a file at `config/initializers/generators.rb` that says when a scaffold is generated, don’t generate files for
fixtures, view specs, helper specs, routing specs, request specs or controller
specs.

To apply your template, use the `-m` flag and pass in the location of the template (either a file or a URL)

```
$ rails new blog -m ~/template.rb
$ rails new blog -m http://example.com/template.rb
```
