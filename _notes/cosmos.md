Initial bundle checkout:
bundle
bundle exec rake build spec

Subsequent tests:
bundle exec rake

Testing locally:
gem uninstall cosmos
gem build cosmos.gemspec
gem install cosmos-0.0.0.gem
