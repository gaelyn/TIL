Reference: [The return Keyword in Ruby](https://medium.com/rubycademy/the-return-keyword-in-ruby-df0a7f578fcb)

## Explicit
Explicit `return` allows the developer to explicitly stop the execution flow of a method and return a specific value.
```ruby
def explicit_return_call
  puts 'before return call'

  return 'return call'

  puts 'after return call'
end

puts explicit_return_call
```
produces:  
```
before return call
return call
```
`return` will return `nil` if no value is passed as an argument.
```ruby
def return_without_value
  return
end

return_without_value # => nil
```

## Implicit
Implicit `return` is when Ruby returns the value of the last executed instruction in the method
```ruby
def implicit_return
  if true
    42
  else
    0
  end
end

implicit_return # => 42

def rom_ebook
  'Ruby Object Model - eBook'
end

rom_ebook # => "Ruby Object Model - eBook"
```

## Return and Assignment Methods.
```ruby
class MyClass
  def x=(y)
    return 42    # => the return is processed but the return value is igonred.
    puts 'hello' # => never called.
  end
end

p MyClass.new.x = 21 # => 21
```
`return` is processed but the value is ignored.  

## Unexpected Return
The `return` keyword can only be used within a method. A call to `return` outside of a method raises a `LocalJumpError`
