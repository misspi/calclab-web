require 'rake/clean'
require 'yaml'
require 'erb'

site = YAML::load(File.open('site.yml'))
site.each_key {|n| site[n.to_sym] = site[n]}

class Site
  def render
    
  end
end

ASSETS = ['css', 'images', 'javascript']

CLEAN << 'output'

desc "generate files"
task :site => :assets do
  puts "Building #{site[:name]}..."
  template_file = File.join site[:source], site[:template]
  puts template_file
  template = ERB.new(File.read(template_file))
  builder = Site.new
  puts template.run(builder.get_binding)
end

desc "Copy assets to ouput directory"
task :assets => :directories do
  ASSETS.each do |asset|
    folder = File.join site[:source], asset
    length = site[:source].length
    FileList["#{folder}/**/*"].each  do |source|
      target = File.join site[:output], source[length..source.length]
      cp source, target
    end
  end
end

desc "Create output directories"
task :directories do
  puts "Creating directories..."
  create_dir(site[:output])
  ASSETS.each {|rel| create_dir(File.join(site[:output], rel))}
end

def create_dir(dir)
  if !File.exists? dir
    puts "Creating directory #{dir}..."
    Dir.mkdir(dir)
  end
end


task :default => 'site'