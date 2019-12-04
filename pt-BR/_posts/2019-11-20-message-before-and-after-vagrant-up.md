---
layout: post
title: Mostrar mensagens vagrant up
subtitle: Message before and after vagrant up
description: Mensagem antes e depois vagrant up.
categories: vagrant
image: /img/blog/message-before-and-after-vagrant-up.jpeg
date: 2019-11-21 10:00:00
comments: true
published: true
tags: tutorial vagrant laravel vagrant&nbsp;up messages&nbsp;vagrant vagrant&nbsp;provision vagrantfile post_up_message
link_ref: message-before-and-after-vagrant-up
---

Abaixo está um exemplo muito simples de como exibir uma mensagem antes e depois da instalação. É muito útil para obter instruções sobre como acessar vários componentes do ambiente de desenvolvimento.

## Início

As configurações devem ser feitas no seu `vagrantfile`. É muito simples:

## Exemplo

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

## Resultado

Agora é só executar `vagrant up` em seu terminal para ver o resultado
