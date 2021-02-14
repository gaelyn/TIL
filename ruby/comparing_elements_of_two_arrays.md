## How to compare elements of two arrays according to position

If you need to compare two arrays and it's dependent on what position they're in, the .zip method comes in handy.

Example:
```ruby
@codemaker.code = ["R", "R", "G", "B"]
@codebreaker.guess = ["Y", "R", "B", "R"]

def num_correct_positions
  @zip = @codemaker.code.zip(@codebreaker.guess)
  #=> [["R", "Y"], ["R", "R"]["G", "B"],["B", "R"]]

  @num_correct_positions = @zip.select do |array|
    array[0] == array[1]
    #=> [["R", "R"]]
  end
  @num_correct_positions.count
  #=> 1
end
```
