--- 
:layout: post
:title: Installation of Jekyll on Fedora
:date:   2023-11-19 22:35:51 +0100
:categories: jekyll ruby fedora
---

Install ruby with rbenv on Fedora

```sh
sudo dnf install rbenv ruby-build --setopt=install_weak_deps=False
sudo yum install -y gcc patch bzip2 openssl-devel libyaml-devel libffi-devel readline-devel zlib-devel gdbm-devel ncurses-devel
git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build
rbenv install 3.2.2
rbenv local 3.2.2
rbenv exec bundle install
rbenv exec gem install jekyll-asciidoc coderay
rbenv exec gem install jekyll-github-pages-gem
rbenv exec jekyll build --drafts --watch
```

Normal small Jekyll installation

```sh
rbenv exec jekyll new --skip-bundle .
bundle update github-pages
rbenv exec bundle install
rbenv exec bundle update github-pages
```

Perhaps this will install adoc support for Jekyll.

```sh
sudo dnf install rbenv ruby-build --setopt=install_weak_deps=False
sudo yum install -y gcc patch bzip2 openssl-devel libyaml-devel libffi-devel readline-devel zlib-devel gdbm-devel ncurses-devel
git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build
rbenv install 3.2.2
rbenv local 3.2.2
rbenv exec bundle install
rbenv exec gem install jekyll-asciidoc coderay
rbenv exec gem install jekyll-github-pages-gem
rbenv exec jekyll build --drafts --watch
```

----
