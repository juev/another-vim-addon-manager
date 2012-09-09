require "yaml"

FNAME = "plugins.yaml"

if File.exist?(FNAME)
  @plugins_url = YAML::load_file(FNAME)
else
  @plugins_url = [ "https://github.com/tpope/vim-pathogen" ]
  File.open(FNAME, "w") { |f| f.write(@plugins_url.to_yaml) }
end

unless File.exist?("bundle")
  Dir.mkdir("bundle")
end

desc "Install new and remove excess plugins in bundle directory"
task :default => [:clean, :install]

desc "Remove excess plugins in bundle directory"
task :clean do
  puts red("Clean plugins in ~/.vim/bundle")
  @plugins = @plugins_url.map { |url| parse_url(url) }
  Dir.foreach("bundle").drop(2).each do |name|
    if not @plugins.include?(name)
      puts "#{red('[Removing]')} #{name}"
      FileUtils.rm_rf("bundle/#{name}")
    end
  end
end

desc "Install new plugins in bundle directory"
task :install do
  @plugins_url.each do |url|
    if File.exists?("bundle/#{parse_url(url)}")
      print green('[Exists] ') + parse_url(url) + "\n"
    else
      print green('[Installing] ') + parse_url(url) + "\n"
      system("git clone -q #{url} bundle/#{parse_url(url)}")
    end
  end
end

desc "Update plugins in bundle directory"
task :update do
  # puts green("Update plugins in ~/.vim/bundle")
  Dir.foreach("bundle").drop(2).each do |plugin|
    print green("[Update] ") + plugin + "\n"
    Dir.chdir("bundle/"+plugin) do
      system("git pull -q")
    end
  end
end

desc "List plugins in bundle directory"
task :list do
  puts green("Plugins installed in ~/.vim/bundle")
  Dir.foreach("bundle").drop(2).each { |plugin| puts plugin }
end

def parse_url(name)
  name.split('/').last.split('.git').first
end

def red(text)
  "\033[31m#{text}\033[0m"
end

def green(text)
  "\033[36m#{text}\033[0m"
end
