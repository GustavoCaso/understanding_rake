require 'rake'

source_files = Rake::FileList.new('**/*.md', '**/*.markdown') do |fl|
  fl.exclude(%r{^scratch/})
  fl.exclude do |f|
    `git ls-files #{f}`.empty?
  end
end

task default: :html

task html: source_files.ext('.html')

rule '.html' => '.md' do |t|
  sh "pandoc -o #{t.name} #{t.source}"
end

rule '.html' => '.markdown' do |t|
  sh "pandoc -o #{t.name} #{t.source}"
end
