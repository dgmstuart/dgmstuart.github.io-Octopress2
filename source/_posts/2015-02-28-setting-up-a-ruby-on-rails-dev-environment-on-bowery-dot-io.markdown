---
layout: post
title: "Setting up a Ruby dev environment on Bowery.io"
date: 2015-02-28 01:27:44 +0000
comments: true
categories: [ruby]
published: false
---

TODO: post this blogpost here:
https://groups.google.com/forum/#!topic/bowery/I-YBrEZRKjk


[Bowery.io](http://bowery.io/) is a hosted development environment service.
The idea is that you edit your files locally, but run your code in a cloud-hosted
[Docker](https://www.docker.com/) container, based on an image which can be
shared and edited by teams.

It looks like it used to host its own packages and allow environments to be
set up through a gui, but now the approach is to either install everything by
hand or use a dockerfile, which I guess makes sense as docker has become more
and more popular and Bowery's main audience is going to be quite devvy devs

Approach: Use a dockerfile
--------------------------

Approach: Install ruby directly
-------------------------------
Not having ever used docker in anger, my first attempt involved just
installing ruby manually. The following steps are
basically a textbook set of steps for installing ruby on a new Ubuntu machine
(which is what Bowery instances are based on):

1. Update apt-get:

        apt-get update

2. [Install the dependencies for ruby-build](https://github.com/sstephenson/ruby-build/wiki#suggested-build-environment)
using apt-get

2. [Install rbenv](https://github.com/sstephenson/rbenv)

3. [Install ruby-build](https://github.com/sstephenson/ruby-build)

4. Install ruby with rbenv:

        rbenv install 2.2.0
        rbenv global 2.2.0

5. Install bundler:

        gem install bundler

