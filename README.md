# [Philips Hue API — Unofficial Reference Documentation](http://burgestrand.github.com/hue-api)

Philips Hue API reference documentation, created by sniffing network traffic, a
lot of guessing, and interpreting and trying out what others have discovered at:

- [Hack the Hue](http://rsmck.co.uk/hue)
- [A Day with Philips Hue](http://www.nerdblog.com/2012/10/a-day-with-philips-hue.html?showComment=1352172383498)
- [Philips Hue Lightbulb API Documentation](http://blog.ef.net/2012/11/02/philips-hue-api.html)

There is a mailing list, dedicated to discussions and questions about hacking
the Philips Hue and related protocols.

- Mailing list web interface: <https://groups.google.com/d/forum/hue-hackers>
- Mailing list e-mail address: <hue-hackers@googlegroups.com>

This repository was forked from the [GitHub API v3 documentation][].  It’s a
static site built with [nanoc][], and is published to <http://burgestrand.github.com/hue-api>
for hosting via [GitHub Pages][].

All submissions are welcome. To submit a change, fork this repo, commit your
changes, and send us a [pull request](http://help.github.com/send-pull-requests/).
Successful pull requests result in commit access to the repository.

[nanoc]: http://nanoc.stoneship.org/
[GitHub Pages]: http://pages.github.com/
[GitHub API v3 documentation]: https://github.com/github/developer.github.com

## Setup

Ruby 1.8 or newer is required to build the site. Most modern operating systems
come with ruby 1.8.5 (or newer) pre-installed, which should suffice. On Windows
you can install ruby with [RubyInstaller](http://rubyinstaller.org/).

You’ll also need the [bundler ruby gem][] to install the dependencies required
for building the site.

```shell
gem install bundler # install bundler
bundle install # install dependencies with bundler
```

You can see the available commands with rake:

```shell
rake -T
```

If you are mainly concerned with adding or modifying content, the rake tasks interesting
to you are:

- `rake compile`, compiles the site into `output/` directory.
- `rake server`, starts a server on port 3000 for viewing the site locally.

[bundler ruby gem]: http://gembundler.com/

## Styleguide

Not sure how to structure the docs?  Here's what the structure of the
API docs should look like:

    ---
    title: API title
    ---

    # API title

    Description about the API.

    <%= toc %>

    ## API endpoint title

    <%= http 'VERB /api/:username/endpoint' %>

    ### Parameters (optional header)

    name
    : description

    ### Input (example request json body)

    <%= json :field => "sample value" %>

    ### Response

    <% json do %>
    { "some": "json" }
    <% end %>

**Note**: We're using [Kramdown Markdown extensions](http://kramdown.rubyforge.org/syntax.html), such as definition lists.

### JSON Responses

We specify the JSON responses in ruby so that we don't have to write
them by hand all over the docs. You can specify it as a ruby object,
or within a block.

```erb
<%= json [{ success: true }] %>
```

```erb
<% json do %>
{
  "1":{
    "name":"Frukost on f 423043           "
  }
}
<% end %>
```
