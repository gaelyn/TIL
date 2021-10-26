[Testing Your Mailers](https://guides.rubyonrails.org/testing.html#testing-your-mailers)

Send the email, then test that it got queued
```ruby
    assert_emails 1 do
      email.deliver_now
    end
```

Test email contains expected sender, reciever, and subject
```ruby
    assert_equal ["me@example.com"], email.from
    assert_equal ["friend@example.com"], email.to
    assert_equal "You have been invited by me@example.com", email.subject
```

Test the body of the email
```ruby
assert_match "The is the body of the email sent to #{@user.name}", email.body.encoded
```
