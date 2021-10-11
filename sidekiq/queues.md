[Tips on Sidekiq Queues](https://phil.tech/2016/tips-on-sidekiq-queues/)
> Defining multiple queues in your Sidekiq config does not distribute work evenly between them.

This config will complete work in queues from the top down. Work in critical will get be completed before default gets looked at and then all work in other queues must be completed before emails get sent.
```
:queues:
  - critical
  - default
  - low
  - mailers
```

The following config just tells which queue should get more attention. Critical is 3 times more likely to get checked, default and mailers are on the same level and twice as likely to get run as low.
```
:queues:
  - [critical, 3]
  - [default, 2]
  - [low, 1]
  - [mailers, 2]
```

[Sidekiq Good Practices](https://longliveruby.com/articles/sidekiq-good-practices)
