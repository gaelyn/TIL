[Source post](https://blog.toshima.ru/2020/02/13/how-to-rollback-migration-in-rails.html)

- Rollback last migration  
`$ rails db:rollback STEP=1`
- Rollback specific migration  
`$ rails db:migrate:down VERSION=20200905201547`
