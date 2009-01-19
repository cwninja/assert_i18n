require 'rubygems'
require 'rake'
require 'rake/testtask'
require 'rake/gempackagetask'

desc 'Default: run unit tests.'
task :default => :test

desc 'Test the plugin.'
Rake::TestTask.new(:test) do |t|
  t.libs << 'lib'
  t.pattern = 'test/**/*_test.rb'
  t.verbose = true
end

spec = Gem::Specification.new do |s|
  s.name        = "assert_i18n"
  s.version     = "0.4"
  s.summary     = "A collection of `I18n` assertions I use in daily life."
  s.description = "A collection of `I18n` assertions I use in daily life."

  s.files        = FileList['[A-Z]*', 'lib/**/*.rb', 'test/**/*.rb', 'rails/*']
  s.require_path = 'lib'
  s.test_files   = Dir[*['test/**/*_test.rb']]

  s.has_rdoc         = true
  s.extra_rdoc_files = ["README.textile"]
  s.rdoc_options = ['--line-numbers', '--inline-source', "--main", "README.textile"]

  s.authors = ["Tom Lea", "Craig Smith"]
  s.email   = %q{commits@tomlea.co.uk}

  s.platform = Gem::Platform::RUBY
end

Rake::GemPackageTask.new spec do |pkg|
  pkg.need_tar = true
  pkg.need_zip = true
end

desc "Clean files generated by rake tasks"
task :clobber => [:clobber_package]

desc "Generate a gemspec file"
task :gemspec do
  File.open("#{spec.name}.gemspec", 'w') do |f|
    f.write spec.to_ruby
  end
end
