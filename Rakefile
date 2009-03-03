require 'rake'
require 'rake/testtask'
begin
  require 'rubygems'
  require 'hanna/rdoctask'
rescue LoadError
  require 'rake/rdoctask'
end

begin
  require "load_multi_rails_rake_tasks"
rescue LoadError
  puts "sudo gem install relevance-multi_rails -s http://gems.github.com/"
  exit(1)
end

task :rcov do
  system "rcov --exclude /Library/Ruby/ --exclude ~/ -Itest `find test/ | grep _test`"
end

desc 'Default: run unit tests.'
task :default => :test

desc 'Test the moonshine plugin.'
Rake::TestTask.new(:test) do |t|
  t.libs << 'lib'
  t.libs << 'test'
  t.pattern = 'test/**/*_test.rb'
  t.verbose = true
end

desc 'Generate documentation for the moonshine plugin.'
Rake::RDocTask.new(:rdoc) do |rdoc|
  rdoc.rdoc_dir = 'rdoc'
  rdoc.title    = 'Moonshine'
  rdoc.options << '--line-numbers' << '--inline-source'
  rdoc.rdoc_files.include('README.rdoc')
  rdoc.rdoc_files.include('lib/**/*.rb')
  rdoc.main = "README.rdoc"
end