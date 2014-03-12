require 'date'

namespace "post" do
  desc "Given a title as an argument, create a new post file"
  task :new, [:title] do |t, args|
    now = DateTime::now().to_date()
    post_date= now || Time.new.strftime("%Y-%m-%d %H:%M:%S %Z")
    filename = "#{now.strftime}-#{args.title.gsub(/\s/, '_').downcase}.markdown"
    path = File.join("_posts", filename)
    if File.exist? path; raise RuntimeError.new("Won't clobber #{path}"); end
    File.open(path, 'w') do |file|
      file.write <<-EOS
---
layout: post
title: #{args.title}
date: #{post_date}
---
Content goes here
EOS
    end
    puts "Now open #{path} in an editor."
  end
end