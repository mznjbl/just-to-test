source "https://rubygems.org"

# This gem pins Jekyll + plugin versions to exactly what GitHub Pages
# runs on their servers, so what you see locally matches what gets
# published. You don't need to touch this file.
gem "github-pages", group: :jekyll_plugins

group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
  gem "jekyll-sitemap"
end

# Windows/JRuby compatibility (harmless to leave in on Mac/Linux)
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw]
gem "webrick"
gem "csv"
gem "logger"
gem "base64"
gem "ostruct"
