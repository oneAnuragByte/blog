This should be fun.
[Read more here](https://oneanuragbyte.github.io/blog/about/)

*****
<br>

# Ubuntu
To setup a new environment for this blog editing, follow the steps in the site below to get environment ready:
ref: https://jekyllrb.com/docs/installation/ubuntu/

1. Run below to install Ruby and other prerequisites:
    ```
    sudo apt-get install ruby-full build-essential zlib1g-dev
    ```
2. Set gem installation path:
    ```
    echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
    echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
    echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
    source ~/.bashrc
    ```

3. Install jekyll and Bundler:
    ```
    gem install jekyll bundler
    ```
    *Follow the YouTube playlist [Up and Running with GitHub Pages](https://www.youtube.com/watch?v=EvYs1idcGnM&list=PLWzwUIYZpnJuT0sH4BN56P5oWTdHJiTNq) by Bill Raymond for detailed explanantion on using jekyll for blogging in markdown*

4. Install bundle
    ```
    bundle install
    ```
5. Run the project and see a live preview of changes and edits
    ```
    bundle exec jekyll serve --livereload
    ```
    *might also have to install 2 more gems, if the new machine does not recognize it using the command `gem install kramdown rouge`*