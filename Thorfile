# borrowed and modified from sinatra.github.com/Thorfile
require "fileutils"

class Blog < Thor
  TEMPLATE = (<<-TEXT).gsub(/^ +/, '')
    ---
    layout: post
    title: TITLE
    author: {{site.author}}
    author_url: http://psa.idiumb.com
    date: #{Time.now.strftime('%A, %B %d, %Y')}
    has_comments: true
    ---

    POST CONTENT HERE
  TEXT

  desc "new", "Create a new blog post and open in EDITOR"
  def new(title=nil)
    abort("usage: thor blog:new 'Post Title'") if title.nil?

    post = TEMPLATE.sub('TITLE', title)
    date = Time.now.strftime('%Y-%m-%d')
    file = "blog/_posts/#{date}-#{title.downcase.gsub(/[!.,;:+=-]/, '').gsub(/\W+/, '-')}.md"
    File.open(file, 'wb') { |f| f.write(post) }
    system "mate #{file}"
  end
end

class Event < Thor
  TEMPLATE = (<<-TEXT).gsub(/^ +/, '')
    ---
    layout: event
    title: TITLE
    author: Jeffrey Alan Huston
    author_url: http://psa.idiumb.com
    date: #{Time.now.strftime('%A, %B %d, %Y')}
    has_comments: true
    ---
    
    POST CONTENT HERE
  TEXT

  desc "new", "Create a new event post and open in EDITOR"
  def new(title=nil)
    abort("usage: thor blog:new 'Post Title'") if title.nil?

    post = TEMPLATE.sub('TITLE', title)
    date = Time.now.strftime('%Y-%m-%d')
    file = "events/_posts/#{date}-#{title.downcase.gsub(/[!.,;:+=-]/, '').gsub(/\W+/, '-')}.md"
    File.open(file, 'wb') { |f| f.write(post) }
    system "mate #{file}"
  end
end