require 'rubygems'
require 'rake'
require 'rake/packagetask'

$: << 'lib'

build_dir = 'build'
theme_name='KerryBuckley'

theme_dir = File.join build_dir, theme_name
stylesheet_dir = File.join theme_dir, 'stylesheets'

desc 'Builds the theme and creates a tarball'
task :default  => [:init, :copy_files, :css, :package]

task :init do
  rm_rf build_dir
  mkdir_p [theme_dir, stylesheet_dir]
end

task :copy_files do
  cp_r Dir.glob('php/*'), theme_dir
  cp_r 'images', theme_dir
end

task :css do
  # load 'compress.rb'
  dir = pwd
  cd 'lib'
  system "ruby compress.rb -pKerryBuckley -o../#{stylesheet_dir}"
  cd dir
end

Rake::PackageTask.new theme_name, :noversion do |p|
  p.need_tar_gz = true
  p.package_dir = 'build'
  p.package_files.include("*")
end
