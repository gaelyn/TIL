Problem:  
Sort function worked with date but not text field. 
```
"name": { "type": "text"}
```
[Source](https://kb.objectrocket.com/elasticsearch/how-to-sort-an-analyzed-text-field-in-elasticsearch)
> The main problem with sorting an analyzed text field is that we lose the original string representation.

>...in the mapping the name field is of type text, which means values like “1 Gallon Vanilla Soy Milk” get analyzed and broken down into their individual terms: “1”, “Gallon”, “Vanilla”, “Soy”, and “Milk”. Unfortunately, this means we wouldn’t be able to sort the values alphabetically

To fix:  
1. Create subfield of type keyword
```
"name": {
  "type": "text",
  "fields": {
    "raw": {
      "type": "keyword"
    }
  }
}
```
2. Sort by the subfield specifying "name.raw" as the field to sort by
```ruby
sort.by("name.raw", order: "asc")
```

See also this [Stack Overflow](https://stackoverflow.com/questions/25195653/elastic-search-alphabetical-sorting-based-on-first-character)