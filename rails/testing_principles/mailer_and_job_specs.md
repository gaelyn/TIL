Quotes from [The Complete Guide to Rails Testing](https://www.codewithjason.com/complete-guide-to-rails-testing/) on why to NOT test mailers and jobs:
> I try very hard to make all my mailers and background jobs one-liners (or close).

> I don’t think mailers and background jobs should do things, I think they should only call things. This is because mailers and background jobs are mechanical devices, not code organization devices.

>To test my mailers and background jobs, I put their code into a PORO model and write tests for that PORO.
