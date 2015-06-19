# This is an example of a Rake Task called "hello_rake"
task :hello_rake do
  puts "Hello, from rake"
end

task :default do
  puts "Hello, from default task!"
end

# loads the environment
task :environment do
  require_relative "config/environment.rb"
end

# defines a prerequisite of environment
# calls User.with_upcoming_todos
task :upcoming_todos => [:environment] do
  User.with_upcoming_todos.each do |user|
    puts "Emailing #{user}"
  end
end

# defines a prerequisite of environment
# calls User.with_overdue_todos
task :overdue_todos => [:environment] do
  User.with_overdue_todos.each do |user|
    puts "Emailing #{user}"    
  end
end

# defines a prerequisite of environment
# calls Todo.mark_overdue
task "todos:mark_overdue" => [:environment] do
  Todo.mark_overdue
end

# defines a prerequisite of environment
# calls Todo.mark_upcoming
task "todos:mark_upcoming" => [:environment] do
  Todo.mark_upcoming
end

# loads the environment
desc "Loads an interactive console."
task :console => [:environment] do
  load './bin/console'
end

#send_summary defines a prerequisite of environment
#send_summary accepts an argument for the user email
#send_summary emails the user a summary
# below are just copies from README
namespace :user do
  desc "Send a summary to a User"
  task :send_summary, [:email] => [:environment] do |t, args|
    puts "Sending summary to user with #{args[:email]}"
  end

  task :todo_reminder => [:environment] do
    my_ruby_home = ENV["MY_RUBY_HOME"]
    puts "ENV includes #{my_ruby_home}"

    puts "Sending todo reminder to #{ENV["EMAIL]"]}"
  end
end


