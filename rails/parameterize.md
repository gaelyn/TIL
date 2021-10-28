if you have a collection of Users something like this:  
`users = [#User name: "Gaelyn Cooper", #User name: "John Doe"]`

```ruby
<% users.each do |user| %>
  <div id="user-<%= user.name.parameterize %>">
    <%= user.do_something %>
  </div>
<% end %>
```
You can "parameterize" the name for the id by calling `.parameterize` which will downcase and replace spaces wtih hyphens.

So `id="user-<%= user.name.parameterize %>"` will be `id="user-gaelyn-cooper"`
