`ActiveRecord::PendingMigrationError`  
If you have pending migrations and want to see them, run `rails db:migrate:status`   
This will give you a list of all migrations. `up` means they've been migrated, `down` means they haven't.
