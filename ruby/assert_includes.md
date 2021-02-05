### MiniTest assert_includes

When building tests, assert_includes is useful to assert whether or not a collection includes a certain element without having to include ALL the elements or knowing what specific order they in inside the collection.  

* assert_equal(collection, obj, msg = nil)  
Fails unless collection includes obj.  
https://docs.ruby-lang.org/en/2.1.0/MiniTest/Assertions.html#method-i-assert_includes


Example from ~./turing/mod1/projects/war_and_peace/turn_test.rb
```ruby
def test_spoils_are_awarded_to_winner
  @turn.pile_cards
  @turn.award_spoils

  assert_equal @player1.deck.cards.count, 5
  assert_equal @player2.deck.cards.count, 3
  assert_includes @player1.deck.cards, @card3
end
```

Here I only needed to know that `@player1.deck.cards` included `@card3` because that was the one that was added in the method.

(Note: I did not include the msg because it was unnecessary/irrelevant)  
