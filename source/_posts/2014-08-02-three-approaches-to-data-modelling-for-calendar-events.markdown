---
layout: post
title: "Three approaches to data modelling for calendar events"
date: 2014-08-02 00:39:30 +0100
comments: true
categories:
published: false
---

Swing Out London [[[link]]] has to deal a problem which faces any moderately complicated system handling calendar events: storing both repeating and one-off events and generating a single list showing both.

The simplest case of repeating events is those which repeat every week, and this happens to be the only case which Swing Out London deals with {{FOOTNOTE: THIS IS A DELIBERATE CHOICE}}

In that case we can express the problem like this:


There are a couple of different ways you might go about managing this:

Approach 1: Calculate at runtime

Do-able with modulo math in the sql

Approach 2: Generate events

Approach 3: Generate instances