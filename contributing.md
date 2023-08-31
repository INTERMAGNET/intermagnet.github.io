# INTERMAGNET contribute

Contributions from INTERMAGNET members to this site are encouraged. This file describes how you can contribute.

## The simple way

You can edit the contents of this site directly in GitHub just using a web browser.
To do this you'll need to get a GitHub account (if you don't already have one) which
you can do [here](https://github.com/join). Then you'll need to get one of the existing
owners of this site to give you access so you are able to edit files.

You can learn how to edit a Markdown file [here](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)
(it's quite simple).

## The comprehensive way

### Description of the recommended github workflow

<https://github.com/INTERMAGNET/intermagnet.github.io/blob/master/docs/git-workflow/README.md>

For more complex changes, you can clone this repository to your own computer, edit there and then upload when you have completed your changes. Files with a .md suffix are 'markdown' files. You can edit these with a text editor and preview them with the Python package 'grip'. Files in the FAQ area use Jekyll templating. You can edit these with a text editor and preview them using the Ruby package 'jekyll'.

### Installing and using grip

1. Install python if you don't already have it. There are instructions [here](https://wiki.python.org/moin/BeginnersGuide/Download).

2. Once you have python installed, then from a command line:

```bash
pip install grip
```

3. Start the page viewer on default port (6419) or on port 12345

```bash
grip
grip 12345
```

4. Use a browser to view the rendered markdown (assuming grip is running on the default port). Here are some example URLs.

    - View README.md (the default file that grip renders):

    ```bash
    http://localhost:6419/
    ```

    - View CONTRIBUTING.md:

    ```bash
    http://localhost:6419/CONTRIBUTING.md
    ```

More information on grip [here](https://github.com/joeyespo/grip).

### Installing and using Jekyll

1. If you don't have Ruby installed, install Ruby 2.1.0 or higher from [here](https://www.ruby-lang.org/en/downloads/).

For Debian 10, you can do this:
```bash
sudo apt-get install ruby ruby-dev make gcc g++ zlib1g zlib1g-dev git
```

2. Using a command shell go to the folder that contains the cloned copy of the repository on your computer and type these commands to install Jekyll:

```bash
gem install bundler
bundle install
```

On a Debian 10 machine where you don't have access to system resources, you can do this instead:

```bash
gem install bundler --user-install
~/.gem/ruby/2.5.0/bin/bundle install --path ~/.gem/
```

3. Run Jekyll like this (from the same folder as step 2). This
   will also compile any changes you make to Jekyll files and
   send them to the target web site:

```bash
bundle exec jekyll serve
```

For the Debian 10 install above, the command to run Jekyll is:

```bash
~/.gem/ruby/2.5.0/bin/bundle exec jekyll serve
```

   More information on Jekyll [here](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/).
   Some useful Jeykll commands (when using Jekyll locally) [here](https://jekyllrb.com/docs/usage/)

4. To view the site in a browser use this URL:

```bash
http://localhost:4000/
```

## Adding new pages and folders

If you need to add new content to the site, you'll need to add a bit of configuration to support your new page.
First add the page or folder to the project.

If you are adding a folder, update the ```_config.yml``` file in the root of the project. Follow how it's done for the 'FAQ' folder. Documentation on the configuration is available [here](https://jekyllrb.com/docs/collections/).

To add a new link to the navigation bar on INTERMAGNET's organization page [https://intermagnet.github.io/](https://intermagnet.github.io/) you need to update ```_data/navs.yml```.
