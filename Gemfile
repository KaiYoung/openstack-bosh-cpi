# Copyright (c) 2012 Piston Cloud Computing, Inc.

source :rubygems
gemspec

gem "rake"

group :development do
  gem "guard"
  gem "guard-bundler"
  gem "guard-rspec"
  gem "guard-yard"
  gem "redcarpet"
  gem "ruby_gntp"
  gem "rb-fsevent"

  gem "ruby-debug", :platforms => :ruby_18
  gem "ruby-debug19", :platforms => :ruby_19
end

group :development, :test do
  gem "ci_reporter"
  gem "rspec", "~>2.10"

  gem "rcov", :platforms => :ruby_18
  gem "simplecov", :platforms => :ruby_19
  gem "simplecov-rcov", :platforms => :ruby_19
end
