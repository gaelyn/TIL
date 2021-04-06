In app/views/show.html.erb underneath a search box
```
<% if (@pet.nil?) %>
  <p>No pets searched</p>
<% else %>
  <p><%= @pet.name %></p>
<% end %>
```
https://stackoverflow.com/questions/3702256/ruby-rails-conditional-search-method-if-else-no-results-found
