# Change Tracker
[![Build Status](https://travis-ci.org/Morred/change_tracker.svg?branch=master)](https://travis-ci.org/Morred/change_tracker)

This gem helps you to track changes to your Active Record models. It's like a very lightweight version of gems like paper_trail, which are awesome but felt like overkill for what I needed at that point in time (specifically a changelog that would just display changes to records, no need for rolling back to earlier versions etc).

It adds a table to your database where it will then proceed to track changes (creating, updating and deleting) to records of the models you want to track. 

This includes the model name and ID of the record as well as the change type (:added_record, :changed_record, :deleted_record) and the data that changed.
When creating or deleting a record, Change Tracker will serialize and save the complete record into the changed_data field, whereas when updating a record it will only save the attributes that have changed.


## Setup

Add the gem to your Gemfile.
```
gem 'change_tracker'
```
Run `bundle install`.

Add a *changes* table to your database:
```
bundle exec rails generate change_tracker:install
bundle exec rake db:migrate
```

## Usage

Include it into the models you want to track like this:

```
class Something < ActiveRecord::Base

  include ChangeTracker

  ...

end
```
That's it!


## Contributing

1. Fork it ( https://github.com/Morred/change_tracker/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request