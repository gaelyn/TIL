While working through the CSV names exploration (~/my_stuff/projects/futbol/csv_exploration), Josh and I were trying to come up with ways to simplify the `where(q)` method which takes a Hash of desired queries as an argument and outputs an array of `Name` results in which all of the query values are `true`.

We had already established a `select_by_query(q)` method that takes an individual query and finds `Names` that match that query.

```ruby
def self.select_by_query(q)
  find_by = q.first
  criteria = q.last.downcase
  all_names.select do |name|
    name.send(find_by) == criteria
  end
end
```
Example:  
```ruby
Name.select_by_query([:bio_gender, "female"])
  => [#<Name:0x00007f99b1fbcdc0 @bio_gender="female", @count="13", @ethnicity="hispanic", @name="geraldine", @rank="75", @year="2011">,
 #<Name:0x00007f99b1fbcaa0 @bio_gender="female", @count="21", @ethnicity="hispanic", @name="gia", @rank="67", @year="2011">,
 #<Name:0x00007f99b1fbc780 @bio_gender="female", @count="49", @ethnicity="hispanic", @name="gianna", @rank="42", @year="2011">, ...
]
```
Back to refactoring the `where` method. We started with `each` and an empty array to accumulate results:

```ruby
def self.where(q)
  results = []
  q.each do |query|
    results = select_by_query(query) if results.empty?
    results = results & select_by_query(query)
  end
  results
end
```
We start with an empty array  
```
results = []
```
The first time through the block results will be set to `select_by_query` of first query
```
query = [:bio_gender, "female"]
results.empty? #=> true
results = [#<Name:0x00007f99b1fbcdc0 @bio_gender="female", @count="13", @ethnicity="hispanic", @name="geraldine", @rank="75", @year="2011">,
#<Name:0x00007f99b1fbcaa0 @bio_gender="female", @count="21", @ethnicity="asian and pacific islander", @name="gia", @rank="67", @year="2011">,
 ...
]
```
Each subsequent iteration will reset `results` to the `Names` where the current `query` intersects with current `results`.
```
query = [ethnicity: 'hispanic']
results.empty? #=> false
results = results & select_by_query(query)
  #=> [#<Name:0x00007f99b1fbcdc0 @bio_gender="female", @count="13", @ethnicity="hispanic", @name="geraldine", @rank="75", @year="2011">,
  #<Name:0x00007f99b1fbcaa0 @bio_gender="female", @count="21", @ethnicity="hispanic", @name="gia", @rank="67", @year="2011">,
   ...
  ]
```

We can then return `results` which will be an array of `Names` where all queries intersect.   

We then simplified this method by using `reduce`:

```ruby
def self.where(q)
  q.reduce([]) do |results, query|
    results = select_by_query(query) if results.empty?
    results & select_by_query(query)
  end
end
```
It essentially works the same as the `each` method, except that we tell it what to set `results` to in the parentheses, put `results` and `query` in the pipes, then after each iteration through the block `results` will act as an accumulator and `~*~*magically*~*~` be set to the last line in the block. 
