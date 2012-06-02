task :default => :build
 
desc 'Build site with Jekyll.'
task :build  => :tags do
	print "Compiling website...\n"
  sh "jekyll"
end

desc 'Enter development mode.'
task :local => :build do
	print "Auto-regenerating enabled.\n"
	print "Development server started at http://localhost:4000/ \n"
	print "Development mode entered.\n"
  sh "jekyll --auto --server"
end

task :new do
  throw "No title given" unless ARGV[1]
  title = ""
  ARGV[1..ARGV.length - 1].each { |v| title += " #{v}" }
  title.strip!
  now = Time.now
  path = "_posts/" + now.strftime('%F') + "-" + title.downcase.gsub(/[\s\.]/, '-').gsub(/[^\w\-]/, '') + ".html"
  
  File.open(path, "w") do |f|
    f.puts "---"
    f.puts "layout: default"
    f.puts "title: #{title}"
    f.puts "date: #{now.strftime('%F %T')}"
    f.puts "speakers:"
    f.puts "    - name:"
    f.puts "      handle:"
    f.puts "      pic:"
    f.puts "      about:"
    f.puts "      website:"
    f.puts "---"
    f.puts ""
    f.puts ""
  end
  
  `open -a Byword #{path}`
  exit
end