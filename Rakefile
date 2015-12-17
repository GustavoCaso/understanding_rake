require 'rake'

SOURCE_FILES = Rake::FileList.new('**/*.md', '**/*.markdown') do |fl|
  fl.exclude(/^scratch\//)
  fl.exclude do |f|
    `git ls-files #{f}`.empty?
  end
end

task default: :html

task html: SOURCE_FILES.ext('.html')

rule '.html' => ->(f){source_for_html(f)} do |t|
  sh "pandoc -o #{t.name} #{t.source}"
end

def source_for_html(html_file)
  # This will return from the SOURCE_FILES array the
  # file with extension which match the file name
  SOURCE_FILES.detect{|f| f.ext('') == html_file.ext('')}
end
