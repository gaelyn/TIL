### Creating a new Hash with array values

To create an array in which you can put values into an array that corresponds with a key, use this syntax:

`new_array_hash = Hash.new { |hash, key| hash[key] = [] }`

Example from turing/mod_1/independent_challenges/potluck/ :

```ruby
def menu
  @menu = Hash.new {|hash, key| hash[key] = []}
  dishes.each do |dish|
    @menu[dish.category] << dish.name
  end
  @menu
end
```

In this instance, I needed a hash that could use the `dish.category` as keys and corresponding values would be arrays of `dish.name`.  

Output looked like this:  
```ruby 
=> {:appetizer=>["Couscous Salad", "Summer Pizza", "Bean Dip"], :entre=>["Roast Pork", "Cocktail Meatballs"], :dessert=>["Candy Salad"]}
```
