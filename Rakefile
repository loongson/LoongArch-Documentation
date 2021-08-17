namespace :book do
    books = FileList['docs/*.adoc']

    desc 'build basic book formats'
    task :all =>[:html, :pdf]

    desc 'build HTML format'
    task :html, [:arg] do |t, args|
        args.with_defaults(:arg => books)
        puts 'Converting to HTML...'
        `bundle exec asciidoctor -v -b html5 -a stylesheet=../themes/html.css -a data-uri -D public #{args[:arg]}`
        puts ' -- HTML conversion done!'
    end

    desc 'build PDF format'
    task :pdf, [:arg] do |t, args|
        args.with_defaults(:arg => books)
        puts 'Converting to PDF... (this will take a while)'
        `bundle exec asciidoctor-pdf -v -a pdf-theme=themes/pdf.yml -a pdf-fontsdir="fonts;GEM_FONTS_DIR" -D public #{args[:arg]}`
        puts ' -- PDF conversion done!'
    end

    desc 'Clean all generated files'
    task :clean do |t|
        rm_rf 'public'
    end
end
