---
layout: post
title:  "Error Installing Nokogiri 1.10.10 when trying to configure Jekyll for GitHub pages"
date:   2020-11-04 01:56:07 +0530
categories: jekyll update
---

While trying to configure Jekyll on WSL on Windows 10, I kept getting errors w.r.t installation of nokogiri 1.10.10. 

    Installing nokogiri 1.10.10 with native extensions
    Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

    current directory:
    /tmp/bundler20201105-857-ez41u7nokogiri-1.10.10/gems/nokogiri-1.10.10/ext/nokogiri
    /usr/bin/ruby2.7 -I /usr/lib/ruby/2.7.0 -r ./siteconf20201105-857-q0bq32.rb extconf.rb
    checking if the C compiler accepts ... yes
    Building nokogiri using packaged libraries.
    Using mini_portile version 2.4.0
    checking for gzdopen() in -lz... no
    zlib is missing; necessary for building libxml2
    *** extconf.rb failed ***
    Could not create Makefile due to some reason, probably lack of necessary
    libraries and/or headers.  Check the mkmf.log file for more details.  You may
    need configuration options.

    Provided configuration options:
            --with-opt-dir
            --without-opt-dir
            --with-opt-include
            --without-opt-include=${opt-dir}/include
            --with-opt-lib
            --without-opt-lib=${opt-dir}/lib
            --with-make-prog
            --without-make-prog
            --srcdir=.
            --curdir
            --ruby=/usr/bin/$(RUBY_BASE_NAME)2.7
            --help
            --clean
            --use-system-libraries
            --enable-static
            --disable-static
            --with-zlib-dir
            --without-zlib-dir
            --with-zlib-include
            --without-zlib-include=${zlib-dir}/include
            --with-zlib-lib
            --without-zlib-lib=${zlib-dir}/lib
            --enable-cross-build
            --disable-cross-build

    To see why this extension failed to compile, please check the mkmf.log which can be found here:

    /tmp/bundler20201105-857-ez41u7nokogiri-1.10.10/extensions/x86_64-linux/2.7.0/nokogiri-1.10.10/mkmf.log

    extconf failed, exit code 1

    Gem files will remain installed in
    /tmp/bundler20201105-857-ez41u7nokogiri-1.10.10/gems/nokogiri-1.10.10 for inspection.
    Results logged to
    /tmp/bundler20201105-857-ez41u7nokogiri-1.10.10/extensions/x86_64-linux/2.7.0/nokogiri-1.10.10/gem_make.out

    An error occurred while installing nokogiri (1.10.10), and Bundler cannot continue.
    Make sure that `gem install nokogiri -v '1.10.10' --source 'https://rubygems.org/'` succeeds before
    bundling.

    In Gemfile:
    github-pages was resolved to 209, which depends on
        jekyll-mentions was resolved to 1.6.0, which depends on
        html-pipeline was resolved to 2.14.0, which depends on
            nokogiri


<br>
I was able to work this though using the link [here](https://nokogiri.org/tutorials/installing_nokogiri.html)

Since I have Ubuntu 20.04 installed over WSL, I used:  

    $ sudo apt-get install build-essential patch ruby-dev zlib1g-dev liblzma-dev


Then run the following as the demand was to install this specific version:

    gem install nokogiri -v '1.10.10'

After this the installation/configuration went smoothly.

Happy blogging...
