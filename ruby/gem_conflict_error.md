Error message I got after attempting to run tests was the following:
```
/Users/gjc/.rbenv/versions/2.5.3/lib/ruby/site_ruby/2.5.0/rubygems/specification.rb:2247:in `raise_if_conflicts': Unable to activate railties-5.2.6, because activesupport-6.1.4.1 conflicts with activesupport (= 5.2.6) (Gem::ConflictError)
```
Then thought it might be related to ruby versions:
```
$rbenv versions
  system
* 2.5.3 (set by /Users/gjc/.ruby-version)
  2.7.2
```
Josh didn't like `.ruby-version` in root directory:
`rm ~/.ruby-version`
That fixed it. Tests now run! 
