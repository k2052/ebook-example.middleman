require 'pdfkit'
require 'eeepub'

namespace :build do
	desc "builds html using middleman"
	task :html do 
		sh "bundle exec middleman build"
	end

  desc "builds pdf using PDFKIt"
	task :pdf => :html do 
		kit = PDFKit.new(File.new('build/index.html'))
		file = kit.to_file('build/index.pdf')	
	end
  
  desc "build epub using EeePub"
	task :epub => :html do
		epub = EeePub.make do
		  title       'sample'
		  creator     'k2052'
		  publisher   'k2052.me'
		  date        '2014-07-01'
		  identifier  'http://example.com/book/foo', :scheme => 'URL'
		  uid         'http://example.com/book/foo'

		  files ['build/index.html'] 
		end
		epub.save('build/index.epub')
	end

  desc "build mobi using kindlegen"
	task :mobi => [:epub] do
		sh *%W[kindlegen build/index.epub -o index.mobi] do
		end
	end
  
  desc "build all the formats"
	task :all => [:html, :pdf, :epub, :mobi] do
	end
end

desc "builds all the formats"
task :default => "build:all"
