# Personal Website

# Appendix for Configuration

May need to run this before installing rvm

```
sudo apt-get install build-essential openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev automake libtool bison subversion nodejs
```
Then download rvm, following this []()

```
curl -L https://get.rvm.io | bash -s stable --ruby
```

Install ruby, and choose corresponding ruby version
```
rvm install 2.2.2
rvm list
rvm use 2.2.2
ruby -v
```

If `rvm use XXX` returns an exception, claiming that 'use is not a function', then run this:

```
vim ~/.bashrc
```
And Add this line to the last:
```
source ~/.rvm/scripts/rvm
```

Now can follow the commands in this [link](http://jekyllcn.com/)

First still install bundler `gem install jekyll bundler`.

But since we already in a github repo, we can do this instead:

Go to the home directory of repo, create a Gemfile, as what we have added in the repo:

```
source 'https://rubygems.org'
gem 'github-pages', group: :jekyll_plugins
```

Then in the same home directory, run `bundle install`.



### Some Debugging Information on 2023.03.11

At last, run `bundle exec jekyll serve`, and server is on localhost:4000.


- First, Bundle install

- Then, An error occurred while installing eventmachine (1.2.7), and Bundler cannot continue.

- Then,
- gem install eventmachine -v '1.2.7' -- --with-ldflags="-Wl,-undefined,dynamic_lookup"

- ./project.h:119:10: fatal error: 'openssl/ssl.h' file not found

- Then
    - gem install eventmachine -- --with-cppflags=-I/usr/local/opt/openssl/include  

    - ./project.h:119:10: fatal error: 'openssl/ssl.h' file not found


    - Then
        - brew link --force openssl


        - Error: No such keg: /opt/homebrew/Cellar/openssl
            - brew install openssl

        - gem install eventmachine -- --with-cppflags=-I/usr/local/opt/openssl/include
