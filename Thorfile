# borrowed and modified from sinatra.github.com/Thorfile
require "fileutils"

class Blog < Thor
  include Thor::Actions
  TEMPLATE = (<<-TEXT).gsub(/^ +/, '')
    ---
    layout: POST
    title: TITLE
    author_url: http://psa.idiumb.com
    date: #{Time.now.strftime('%A, %B %d, %Y')}
    has_comments: true
    ---

    POST CONTENT HERE
  TEXT

  desc "new [layout]", "Create a new blog post and open in EDITOR. --layout [] 'post' or 'event'"
  method_options :layout => 'post'
  def new(title=nil)
    abort("usage: thor blog:new 'Post Title'") if title.nil?

    post = TEMPLATE.sub('TITLE', title)
    post = post.sub('POST',options[:layout])
    date = Time.now.strftime('%Y-%m-%d')
    file = "blog/_posts/#{date}-#{title.downcase.gsub(/[!.,;:+=-]/, '').gsub(/\W+/, '-')}.md"
    File.open(file, 'wb') { |f| f.write(post) }
    system "mate #{file}"
  end
end