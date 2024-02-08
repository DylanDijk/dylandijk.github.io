# Notes for building website


- To build website locally run in terminal: `be jekyll s`
- To add a post that comes up on the home page run `be jekyll post "My New Post"`

***


I am writing important parts of the workflow of the website building process.  

Main things:
- I am using [`rbenv`](https://github.com/rbenv/rbenv#seamlessly-manage-your-apps-ruby-environment-with-rbenv) as a Ruby version manager. It allows you to choose virtual environments that use a specific Ruby version.
  - I have used the [Basic git checkout method to install `rbenv`](https://github.com/rbenv/rbenv#basic-git-checkout)
  - `.rbenv` directory exists in my home directory
  - There is then further [documentaion](https://github.com/rbenv/rbenv#installing-ruby-versions) on installing Ruby and Ruby gems.
    - Main thing is to set the Ruby version you want for your project and then install the gems. [Commands](https://github.com/rbenv/rbenv#command-reference) provided show how to view/set a Ruby version locally or globally.

Nice explanation of what `rbenv` does, from [How it works Section](https://github.com/rbenv/rbenv#how-it-works) of `rbenv` documentation:
> After `rbenv` injects itself into your PATH at installation time, **any invocation of `ruby`, `gem`, `bundler`, or other Ruby-related executable will first activate `rbenv`**. Then, `rbenv` scans the current project directory for a file named `.ruby-version`. If found, that file determines the version of Ruby that should be used within that directory. Finally, `rbenv` looks up that Ruby version among those installed under `~/.rbenv/versions`.     

- Running `bundle` is equivalent to running [`bundle install`](https://bundler.io/v2.4/man/bundle-install.1.html#DESCRIPTION).

Nice explanation of `bundle` command and Gemfile:

>>Gemfile contains your project dependency on gem(s), that you manually mention with version(s) specified, but those gem(s) inturn depends on other gem(s) which is resolved by bundler automatically.
>
>>Gemfile.lock contain complete snapshot of all the gem(s) in Gemfile along with there associated dependency.
>
>>When you first call bundle install, it will create this Gemfile.lock and uses this file in all subsequent calls to bundle install, which ensures that you have all the dependencies installed and will skip dependency installation.

- To build website locally run in terminal: ` bundle exec jekyll s`
  - [`bundle exec`](https://bundler.io/v2.4/man/bundle-exec.1.html) executes the command, in this case `jekyll s`, with all the gems specified in the `Gemfile` available to the Ruby program(s).
- Documentation for [`jekyll` commands](https://jekyllrb.com/docs/usage/) explains the usage of the `jekyll` commands. `jekyll s` is equivalent to `jekyll serve`,
***

I have also been able to carry out the same workflow as above but on my Windows machine (I used a Linux machine the first time I ran the workflow explained above).

Setting up a Linux environment within in a Windows machine can be done by following this brief [tutorial](https://developer.zendesk.com/documentation/developer-tools/getting-started/setting-up-your-development-environment/#setting-up-a-windows-development-environment).

Once I had the Linux environment set up, I cloned my webpage repo into the Linux file directory system using the Ubuntu environemt via the [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=en-gb&gl=gb&rtc=1).

***

## Customising [Chirpy Theme](https://github.com/cotes2020/jekyll-theme-chirpy)

### Setting up global Tex macros

Whilst trying to write maths in a `_post` I noticed that setting up new commands (e.g `\newcommand{\bxi}{\mathbf{x}_i}`) took up space at the beginning of the post. In addition, it is a bit of a pain to have to set up the  macros on each post.

The chirpy theme uses [MathJax to write mathematics](https://chirpy.cotes.page/posts/text-and-typography/#mathematics). The [`_includes\js-selector.html`](https://github.com/cotes2020/jekyll-theme-chirpy/blob/v5.4.0/_includes/js-selector.html) file (v5.4.0 tag) of the Chirpy theme repository, has a section where we can modify the MathJax configuration. In v5.4.0 of the `_includes\js-selector.html` that is where the MathJax configuration part exists.

We can then add Tex macros here as I have done in [this commit](https://github.com/DylanDijk/dylandijk.github.io/commit/58024f9210da578df678985054f04958b88ac479). This [Section](https://docs.mathjax.org/en/latest/input/tex/extensions/configmacros.html#configmacros-options) of the MathJax documentation describes how you can set-up macros, in the MathJax configuration.

In order to make this change to the `_includes\js-selector.html` file we need to make our own `_includes` folder that includes the `js-selector.html` file. This method is described in the [Overriding theme defaults](https://jekyllrb.com/docs/themes/#overriding-theme-defaults) section, they say:

> With a clear understanding of the theme’s files, you can now override any theme file by creating a similarly named file in your Jekyll site directory.
>
>Let’s say, for a second example, you want to override Minima’s footer. In your Jekyll site, create an _includes folder and add a file in it called footer.html. Jekyll will now use your site’s footer.html file instead of the footer.html file from the Minima theme gem.

## Changes to webpage setup

Edit the _config.yml file to update links, images and text such as name.
Can add description under name by editing the `tagline:` line.

### Changing main image
Select path of image in the line:  
`# the avatar on sidebar, support local or CORS resources`  
in the `_config.yml` file.

***

## Generating favicons
Follow [Tutorial](https://chirpy.cotes.page/posts/customize-the-favicon/). The favicons are stored in the path `assets/img/favicons`.

***

## Adding posts

To add a post that comes up on the home page run `bundle exec jekyll post "My New Post"`.
This is using a [jekyll plugin](https://github.com/jekyll/jekyll-compose), this can be further customised.



## Deployment

Currently using GitHub actions to deploy.
 - Note that the action `actions/checkout@v2` ignores submodules by default (see [Usage](https://github.com/actions/checkout/tree/v2#usage) `submodules` line). For example the `assets/lib` folder is a submodule.
