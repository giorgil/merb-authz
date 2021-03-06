require 'rubygems'
require 'rake/gempackagetask'

require 'merb-core'
require 'merb-core/tasks/merb'
require "spec/rake/spectask"

GEM_NAME = "merb-authz"
GEM_VERSION = "0.1.0"
AUTHOR = "Daniel Neighman"
EMAIL = "has.sox@gmail.com"
HOMEPAGE = "http://merbunity.com/"
SUMMARY = "A plugin that offers authorization for merb-auth"

spec = Gem::Specification.new do |s|
  s.rubyforge_project = 'merb-authz'
  s.name = GEM_NAME
  s.version = GEM_VERSION
  s.platform = Gem::Platform::RUBY
  s.has_rdoc = true
  s.extra_rdoc_files = ["README.textile", "LICENSE", 'TODO']
  s.summary = SUMMARY
  s.description = s.summary
  s.author = AUTHOR
  s.email = EMAIL
  s.homepage = HOMEPAGE
  s.add_dependency('merb', '>= 1.0.3')
  s.add_dependency("merb-auth-core", ">= 1.0.3")
  s.require_path = 'lib'
  s.files = %w(LICENSE README.textile Rakefile TODO) + Dir.glob("{lib,spec}/**/*")
  
end

Rake::GemPackageTask.new(spec) do |pkg|
  pkg.gem_spec = spec
end

desc "install the plugin as a gem"
task :install do
  Merb::RakeHelper.install(GEM_NAME, :version => GEM_VERSION)
end

desc "Uninstall the gem"
task :uninstall do
  Merb::RakeHelper.uninstall(GEM_NAME, :version => GEM_VERSION)
end

desc "Create a gemspec file"
task :gemspec do
  File.open("#{GEM_NAME}.gemspec", "w") do |file|
    file.puts spec.to_ruby
  end
end

desc "Run all specs"
Spec::Rake::SpecTask.new("spec") do |t|
  t.spec_opts = ["--format", "specdoc", "--colour"]
  t.spec_files = Dir["spec/**/*_spec.rb"].sort
  t.rcov = false
  t.rcov_opts << '--sort' << 'coverage' << '--sort-reverse'
  t.rcov_opts << '--only-uncovered'
end
