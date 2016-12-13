#This file is generated by ModuleSync, do not edit.

source ENV['GEM_SOURCE'] || "https://rubygems.org"

# Determines what type of gem is requested based on place_or_version.
def gem_type(place_or_version)
  if place_or_version =~ /^git:/
    :git
  elsif place_or_version =~ /^file:/
    :file
  else
    :gem
  end
end

# Find a location or specific version for a gem. place_or_version can be a
# version, which is most often used. It can also be git, which is specified as
# `git://somewhere.git#branch`. You can also use a file source location, which
# is specified as `file://some/location/on/disk`.
def location_for(place_or_version, fake_version = nil)
  if place_or_version =~ /^(git[:@][^#]*)#(.*)/
    [fake_version, { :git => $1, :branch => $2, :require => false }].compact
  elsif place_or_version =~ /^file:\/\/(.*)/
    ['>= 0', { :path => File.expand_path($1), :require => false }]
  else
    [place_or_version, { :require => false }]
  end
end

# Used for gem conditionals
supports_windows = false

group :development do
  gem 'puppet-lint',                        :require => false
  gem 'metadata-json-lint',                 :require => false, :platforms => 'ruby'
  gem 'puppet_facts',                       :require => false
  gem 'puppet-blacksmith', '>= 3.4.0',      :require => false, :platforms => 'ruby'
  gem 'puppetlabs_spec_helper', '>= 1.2.1', :require => false
  gem 'rspec-puppet', '>= 2.3.2',           :require => false
  gem 'rspec-puppet-facts',                 :require => false, :platforms => 'ruby'
  gem 'mocha', '< 1.2.0',                   :require => false
  gem 'simplecov',                          :require => false, :platforms => 'ruby'
  gem 'parallel_tests', '< 2.10.0',         :require => false if Gem::Version.new(RUBY_VERSION.dup) < Gem::Version.new('2.0.0')
  gem 'parallel_tests',                     :require => false if Gem::Version.new(RUBY_VERSION.dup) >= Gem::Version.new('2.0.0')
  gem 'rubocop', '0.41.2',                  :require => false if Gem::Version.new(RUBY_VERSION.dup) < Gem::Version.new('2.0.0')
  gem 'rubocop',                            :require => false if Gem::Version.new(RUBY_VERSION.dup) >= Gem::Version.new('2.0.0')
  gem 'rubocop-rspec', '~> 1.6',            :require => false if Gem::Version.new(RUBY_VERSION.dup) >= Gem::Version.new('2.3.0')
  gem 'pry',                                :require => false
  gem 'json_pure', '<= 2.0.1',              :require => false if Gem::Version.new(RUBY_VERSION.dup) < Gem::Version.new('2.0.0')
  gem 'fast_gettext', '1.1.0',              :require => false if Gem::Version.new(RUBY_VERSION.dup) < Gem::Version.new('2.1.0')
end

group :system_tests do
  gem 'beaker', *location_for(ENV['BEAKER_VERSION'] || '~> 2.20')                if supports_windows
  gem 'beaker', *location_for(ENV['BEAKER_VERSION'])                             if Gem::Version.new(RUBY_VERSION.dup) >= Gem::Version.new('2.3.0') and ! supports_windows
  gem 'beaker', *location_for(ENV['BEAKER_VERSION'] || '< 3')                    if Gem::Version.new(RUBY_VERSION.dup) < Gem::Version.new('2.3.0') and ! supports_windows
  gem 'beaker-pe',                                                               :require => false if Gem::Version.new(RUBY_VERSION.dup) >= Gem::Version.new('2.3.0')
  gem 'beaker-rspec', *location_for(ENV['BEAKER_RSPEC_VERSION'] || '>= 3.4')     if ! supports_windows
  gem 'beaker-rspec', *location_for(ENV['BEAKER_RSPEC_VERSION'] || '~> 5.1')     if supports_windows
  gem 'beaker-puppet_install_helper',                                            :require => false
  gem 'master_manipulator',                                                      :require => false
  gem 'beaker-hostgenerator', *location_for(ENV['BEAKER_HOSTGENERATOR_VERSION'])
  gem 'beaker-abs', *location_for(ENV['BEAKER_ABS_VERSION'] || '~> 0.1')
end

gem 'puppet', *location_for(ENV['PUPPET_GEM_VERSION'])

# Only explicitly specify Facter/Hiera if a version has been specified.
# Otherwise it can lead to strange bundler behavior. If you are seeing weird
# gem resolution behavior, try setting `DEBUG_RESOLVER` environment variable
# to `1` and then run bundle install.
gem 'facter', *location_for(ENV['FACTER_GEM_VERSION']) if ENV['FACTER_GEM_VERSION']
gem 'hiera', *location_for(ENV['HIERA_GEM_VERSION']) if ENV['HIERA_GEM_VERSION']


# Evaluate Gemfile.local if it exists
if File.exists? "#{__FILE__}.local"
  eval(File.read("#{__FILE__}.local"), binding)
end

# Evaluate ~/.gemfile if it exists
if File.exists?(File.join(Dir.home, '.gemfile'))
  eval(File.read(File.join(Dir.home, '.gemfile')), binding)
end

# vim:ft=ruby
