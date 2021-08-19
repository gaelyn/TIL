Based off [this post](https://alvinalexander.com/blog/post/ruby/how-sort-ruby-array-objects-multiple-class-fields-attributes/)

You can sort an array of objects by two or more class attributes as follows

Sort by Gender and then by Last Name
```ruby
def self.sort_gender
  sorted = all_files.sort_by do |person|
    [person.gender, person.last_name]
  end
end
```

Sort by Birthdate and then by Last Name  
Note: handy way to sort by birthdate in a string format and/or M/D/Y format

```ruby
def self.sort_birthdate
  sorted = all_files.sort_by do |person|
    dob = person.dob.split("/")
    [dob[2].to_i, dob[0].to_i, dob[1].to_i, person.last_name]
  end
end
```
