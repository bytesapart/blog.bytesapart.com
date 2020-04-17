# filename: Rakefile
task :default do
    puts "Running CI tasks..."
  
    # Runs the jekyll build command for production
    # TravisCI will now have a site directory with our
    # statically generated files.
    sh("JEKYLL_ENV=production bundle exec jekyll build")
    sh("ls -lrt -d -1 $PWD/{*,.*}")
    puts "Jekyll successfully built"
  end