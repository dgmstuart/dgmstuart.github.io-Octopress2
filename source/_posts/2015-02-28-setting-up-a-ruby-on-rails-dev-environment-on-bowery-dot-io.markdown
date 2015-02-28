---
layout: post
title: "Setting up a Ruby on Rails dev environment on Bowery.io"
date: 2015-02-28 01:27:44 +0000
comments: true
categories: [ruby]
published: false
---
Approach: Install ruby directly
===============================

1. Update apt-get:

        apt-get update

2. [Install the dependencies for ruby-build](https://github.com/sstephenson/ruby-build/wiki#suggested-build-environment)
using apt-get

2. [Install rbenv](https://github.com/sstephenson/rbenv)

3. 3. [Install ruby-build](https://github.com/sstephenson/ruby-build)

4. Install ruby with rbenv:

        rbenv install 2.2.0
        rbenv global 2.2.0

5. Install bundler:

        gem install bundler
