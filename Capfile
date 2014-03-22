# Load DSL and Setup Up Stages
require 'capistrano/setup'

# Includes default deployment tasks
require 'capistrano/deploy'

# Includes tasks from other gems included in your Gemfile
#
# For documentation on these, see for example:
#
#   https://github.com/capistrano/rvm
#   https://github.com/capistrano/rbenv
#   https://github.com/capistrano/chruby
#   https://github.com/capistrano/bundler
#   https://github.com/capistrano/rails
#
# require 'capistrano/rvm'
# require 'capistrano/rbenv'
# require 'capistrano/chruby'
require 'capistrano/bundler'
# require 'capistrano/rails/assets'
# require 'capistrano/rails/migrations'
#require 'capistrano/facter/facter'
require 'capistrano/hiera/hiera'

# Loads custom tasks from `lib/capistrano/tasks' if you have any defined.
Dir.glob('lib/capistrano/tasks/*.cap').each { |r| import r }

require 'capistrano/modules'

set :hiera_config, 'config/hiera.yaml'
set :hiera_data, 'deployment/hiera'
set :puppet_data, 'deployment/puppet'
set :server_data, 'deployment/server'
set :ssh_data, 'deployment/ssh'
set :vagrant_data, 'deployment/vagrant'

#build hiera
hiera_build_servers_from_stage ARGV[0]

#set ssh_options via hiera
set :ssh_options, hiera('ssh_options')
