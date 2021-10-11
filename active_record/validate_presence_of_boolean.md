[Rails Guides reference](https://guides.rubyonrails.org/active_record_validations.html#presence)
> Since false.blank? is true, if you want to validate the presence of a boolean field you should use one of the following validations:
```
validates :boolean_field_name, inclusion: [true, false]
validates :boolean_field_name, exclusion: [nil]
```

Problem:
Getting the following error when `admin` was set as `false`
```
ActiveRecord::RecordInvalid: Validation failed: Admin can't be blank
```

Changed `validates :admin, presence: true` to `validates :admin, inclusion: [true, false]` and tests pass.
