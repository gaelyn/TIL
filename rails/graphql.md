## Setup Graphql for rails
- [rubydocs for graphql](https://www.rubydoc.info/gems/graphql/Graphql/Generators/MutationGenerator)
- `rails new <project name> --api -T -d="postgresql" --skip-spring --skip-turbolinks`
- `bundle add graphql` or just add it to Gemfile  
- `bundle add graphiql-rails` or just add it to Gemfile   
- `rails g graphql:install`  
- Create `app/assets/config/manifest.js` file. Inside this file type  
```
//= link graphiql/rails/application.css
//= link graphiql/rails/application.js
```
- Inside of `config/application.rb` uncomment `require "sprockets/railtie"`
- In `routes.rb` type
```
Rails.application.routes.draw do
  if Rails.env.development?
    mount GraphiQL::Rails::Engine, at: '/graphiql', graphql_path: "graphql#execute"
  end
  post "/graphql", to: "graphql#execute"
end
```  
- generate models example: `rails g model Post title:string body:text``rails g model Author name``rails g migration add_author_to_posts author:references`
`rails db:migrate`  
Models should look like this:
```
class Post < ApplicationRecord
  blongs_to :author
end
```
```
class Author < ApplicationRecord
  has_many :posts
end
```

- `rails g graphql:object Post title:String body:Text author:references`
- `rails g graphql:object Author name:String post:has_many`
- Add some data from `rails c` or in `seeds.rb`
- Open `app/graphql/types/query_type.rb` and add
```ruby
field :posts, [Types::PostType], null: false do
  description "Query that selects all posts."
end

field :postsCount, Integer, null: false do
  description "Query that returns the total number of posts."
end

def posts
  return Post.all
end

def postsCount
  return Post.count
end
```
- In command line run `rails g graphql:mutation CreateAuthorMutation` then `rails g graphql:mutation CreatePostMutation`
- open `app/graphql/mutations/create_post.rb`


- run `rails s` to start server   
- in browser open localhost:3000/graphiql
