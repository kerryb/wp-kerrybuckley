require 'rubygems'
require 'rake'

$: << 'lib'

build_dir = 'build'
theme_name='KerryBuckley'

theme_dir = File.join build_dir, theme_name
stylesheet_dir = File.join theme_dir, 'stylesheets'

desc 'Builds the theme and creates a tarball'
task :default  => [:init, :copy_files, :css]

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
  cd 'lib'
  system "ruby compress.rb -o../#{stylesheet_dir}"
end