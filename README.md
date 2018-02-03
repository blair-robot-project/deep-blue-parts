Parted
============

Parted (Part Editor) is a web-based system for tracking parts through the design and manufacture cycle. It assigns
part numbers with which CAD files can be saved to version control and stores information about parts'
current manufacturing status.

Parted is written in Ruby using the [Sinatra](http://sinatrarb.com) framework and uses MySQL as the
backing datastore. Development and production are run on UNIX (OS X and Ubuntu), so there are no guarantees
it'll work on Windows, sorry.

Parted is a modified version of Deep Blue Parts, which is itself a modification of Cheesy Parts, a wonderful tool written by Pat Fairbank at [Team 254](https://github.com/Team254).

## Team 449 Specific Features

Our fork differs from 199's in a few ways:

1. Ordering is enabled, since we use it.
1. Trello and Slack linked to empty boards since we use Basecamp.

## Development

Prerequisites:

* Ruby 2.3 and development packages
* [Bundler](http://gembundler.com)
* MySQL and development packages
* g++ (perhaps)

To run Parted locally:

1. Create an empty MySQL database and a user account with full permissions on it.
1. Populate `config.json` with the parameters for the development and production environments. Set
`enable_wordpress_auth` to false and `members_url` to blank; they are used for a single sign-on (SSO)
mechanism specific to Team 254. Make sure to add your Slack and Trello API tokens if using those features.
1. Run `bundle install`. This will download and install the gems that Parted depends on.
1. Run `bundle exec rake db:migrate`. This will run the database migrations to create the necessary tables in
MySQL.
1. Run `ruby parts_server_control.rb <command>` to control the running of the parted server, where
`<command>` can be one of `start`|`stop`|`run`|`restart`.

The database migration will create an admin account (username "deleteme@team199.org", password "shark-tank")
that you can use to first get into the system and create other accounts. It is highly recommended that you
delete this account after having created your own admin account.

Uploads are stored in `uploads/` and at this time can only be directly managed by logging into your server.

## Contributing

If you have a suggestion for a new feature in Cheesy Parts, create an issue on GitHub or shoot an e-mail to
[pat@patfairbank.com](mailto:pat@patfairbank.com). Or if you have some Ruby-fu and are feeling adventurous,
fork this or the original repo  and send a pull request. If you are interested in modifying or using our fork, don't hesitate to reach out.

## License

This project lives under the BSD 2-Clause license, found in LICENSE.md. 
