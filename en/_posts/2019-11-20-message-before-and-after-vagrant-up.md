---
layout: post
title: Show messages vagrant up
subtitle: Message before and after vagrant up
date: 2019-11-21 10:00:00
categories: vagrant
description: Simple example of how to display a message before and after vagrant up.
image: /img/blog/message-before-and-after-vagrant-up.jpeg
comments: true
published: true
tags: tutorial vagrant laravel vagrant&nbsp;up messages&nbsp;vagrant vagrant&nbsp;provision vagrantfile post_up_message
link_ref: message-before-and-after-vagrant-up
---

Below is a very simple example of how to display a message before and after vagrant up. It is very useful for instructions on how to access various components of the development environment.

## Basic Usage

Settings must be made in your `vagrantfile`. The use is very simple:

## Example

<pre><code>$mstart = <<MSG
.                                                    .
--                                                  --
-----                                            -----
--------                                      --------
------------------------------------------------------
------------------------------------------------------
-------------------Start of Changes-------------------
------------------------------------------------------
------------------------------------------------------
--------                                      --------
-----                                            -----
--                                                  --
.                                                    .
MSG

$mend = <<-HEREDOC
.                                                    .
--                                                  --
-----                                            -----
--------                                      --------
------------------------------------------------------
------------------------------------------------------
-------------------End of Changes-------------------
------------------------------------------------------
------------------------------------------------------
--------                                      --------
-----                                            -----
--                                                  --
.                                                    .
HEREDOC

Vagrant.configure("2") do |config|

  config.trigger.after :up do |t|
    puts $mstart
  end

  config.vm.post_up_message = $mend

end</code></pre>

## Result

Now just start `vagrant up` to see the result
