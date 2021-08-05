[ruby docs proc](https://ruby-doc.org/core-2.6/Proc.html)

A Proc is an encapsulation of a block of code, which can be stored in a local viariable, passed to a method or another Proc, and can be called

```ruby
ERROR_DESCRIPTION = Proc.new {|code, message| {status: "error | failure", code: code, message: message}}
```
Above code found in [this](https://www.thegreatcodeadventure.com/rails-api-painless-error-handling-and-rendering-2/) article on error handling
