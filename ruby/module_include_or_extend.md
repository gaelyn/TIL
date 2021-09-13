From [this post](http://rubyblog.pro/2017/04/class-methods-and-instance-methods-by-including-one-module)

If we use `include` - all module methods will become instance methods of class.  
If we use `extend` - all module methods become class methods.  

Include example:
```ruby
module Persistence
  def save
    'saving'
  end
end

class User
  include Persistence
end

u = User.new
u.save # => 'saving'
```

Extend example:
```ruby
module Persistence
  def find(id)
    "looking for entity with id=#{id}"
  end
end

class User
  extend Persistence
end

User.find(10) # => looking for entity with id=10
```
