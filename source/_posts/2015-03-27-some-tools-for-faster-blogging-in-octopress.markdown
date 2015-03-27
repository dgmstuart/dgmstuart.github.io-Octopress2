---
layout: post
title: "Some tools for faster blogging in Octopress (and tips for live
blogging)"
date: 2015-03-27 18:48:31 +0000
comments: true
categories:
published: false
---

When I go to conferences and talks I've developed a habit of live-blogging my
notes: taking them in markdown and publishing them with Octopress on this
blog.

I need to be able to start taking notes fast, and publish them even faster
(when a talk finishes, lots of people will be trying to get out of the row of
seats past me!).

Here's my workflow:

1. Open a new post in vim with `newpost "My Post title"`
2. In another terminal window, run `rake isolate[unique words in title]`,
   followed by `rake preview`
3. Start typing, occasionally writing (`:w`) and checking the post in a
   browser window (http://localhost:4000) to make sure the formatting is
   correct
4. As soon as the talk is finished, type `rgd` to publish the post
5. Tweet about the post
6. Find a photo which someone has tweeted of the talk (usually on instagram)
   and add it with `![Speaker speaking at event](Link to photo)`, as well as
   crediting the photographer and linking to their twitter
7. Deploy again (`rgd`) and tweet at the photographer telling them I've done
   so and asking if that's OK
8. When I get a chance, commit and push the source

## Tools for fast blogging
Note that some of those are provided by Octopress, and others are my own
aliases and functions:

### `newpost`
The octopress command for creating a post is `rake new_post["The name of my
post"]`. I'd then typically select the filename it outputs with the mouse,
paste that into the command line and open it with vim. That's _way_ too much
typing, and any seasoned vim user would wince at the word "mouse".

Here's a function which creates the post, isolates it and opens it in one
step:

{% codeblock lang:sh ~/.profile %}
function newpost(){
  cd ${BLOG_HOME:?"Need to set BLOG_HOME to the location of the octopress blog directory"}
  output=$( rake new_post["$@"] )
  echo "$output"

  local return_code=$?
  if [ $return_code -eq 0 ]; then
    # Get the name of the file which was just created and open it:
    post_path=$(grep -o 'source\/_posts\/.*\.markdown' <<< $output)
    # Open with the cursor at the bottom of the header:
    vim -c 'normal G' $post_path
  fi
}
{% endcodeblock %}

My [dotfiles](https://github.com/dgmstuart/dotfiles) are shared between
multiple machines, so the `BLOG_HOME` environment variable is set in a local
profile:

{% codeblock lang:sh ~/.profile.local %}
export BLOG_HOME=$HOME/Dev/Personal/blog
{% endcodeblock %}

I'm pretty new at shell scripting, so if you know of a way to make this better
or more robust, please let me know in the comments.
## Publish and be damned
Notice there's no mention in that of editing. I know that if I held back
publishing until I'd corrected all my mistakes, explained all my ambiguities
and added in links to all the references, I'd never publish anything at all. I
feel like it's much more valuable for those notes to be up as soon as
possible, than for them to be a nicely formed, well-presented narrative.

On top of that, I feel like the main benefit in taking notes is as a form of
[active learning](https://www.linkedin.com/pulse/20130702175823-659753-if-you-aren-t-taking-notes-you-aren-t-learning):
the value is in the process of taking notes, not in the end result.

