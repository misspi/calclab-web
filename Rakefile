require 'rake/clean'

CLEAN << 'output'

desc "generate files"
task :site => :assets do
  
end

task :assets => :directories do

end

task :directories do
  puts "Creating directories..."
  ['output', 'output/css', 'output/images'].each do |folder|
    Dir.mkdir(folder) unless File.exists? folder
  end
end

task :default => 'site'