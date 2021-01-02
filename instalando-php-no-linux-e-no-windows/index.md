---
title:       Instalando o PHP no Linux e no Windows
description: Aprenda como instalar PHP
capitulo:    "php-comecando"
ordem:       4
---

Aqui é uma pequena coleção de receitas para instalação do PHP 8.

Acho que você precisará apenas da primeira.

Ele instala o PHP 8 no wsl2 que é um subsistema do Linux que roda dentro do Windows.

A receita ajudará para quem é do WIndows mas também ajudará você caso queria instalar em uma versão "genuína" Linux Ubuntu.


## Instalando o PHP 8 no wsl2

Você conheçe o [wsl2](https://docs.microsoft.com/pt-br/windows/wsl/install-win10) ?

Ele é um subsistema Linux que roda dentro do Windows.

Este receita serve para o Ubuntu, porém eu executei ela no wsl... e deu tudo certo.

Primeiro, adicione os pacotes PPA:

    sudo add-apt-repository ppa:ondrej/php # Press enter when prompted.
    sudo apt-get update


Instale o PHP8 e o CLI também:

    sudo apt install php8.0-common php8.0-cli -y

Já dá para testar:

    php -v # Show PHP version.
    php -m # Show PHP modules loaded.


Você precisará do Xdebug:

    sudo apt install php8.0-xdebug


Agora você pode escolher entre Apache ou Nginx:

    sudo apt install php8.0-fpm             # Nginx
    sudo apt install libapache2-mod-php8.0  # Apache

Eu fui de Apache.

Fonte:

- [php-8.0-installation-update-guide-debian-ubuntu](https://php.watch/articles/php-8.0-installation-update-guide-debian-ubuntu)


---


Abaxio, deixo registrado algumas receitas mais antigas, acho que você não precisará delas, mas caso precise...


### Debian 8 (Jessie)

Este receita de instalação cobre o __PHP 7__.

No final do arquivo `/etc/apt/sources.list` acrescente o seguinte repositórios...

    # PHP7
    deb http://packages.dotdeb.org jessie all
    deb-src http://packages.dotdeb.org jessie all

Configure a chave gpg.

    wget https://www.dotdeb.org/dotdeb.gpg
    apt-key add dotdeb.gpg

Atualize o sistema.

    apt-get update

Instale através do aptitute

    aptitude install php7.0

---


### Ubuntu 15.4 (Vivid Vervet)

Para instalar o PHP através do __apt-get__ execute o comando abaixo, você precisará ser root ou
utiliza `sudo` antes do comando.

    apt-get install php5

Serão baixados 25 megabytes, aproximadamente. Para testar a instalação execute...

    php -v

Sua tela deve ser parecida com a minha...

    PHP 5.6.4-4ubuntu6 (cli) (built: Apr 17 2015 15:47:51)
    Copyright (c) 1997-2014 The PHP Group
    Zend Engine v2.6.0, Copyright (c) 1998-2014 Zend Technologies
        with Zend OPcache v7.0.4-dev, Copyright (c) 1999-2014, by Zend Technologies


Como visto, a versão instalada é a 5.6.4, porém a versão mais atual é a 5.6.10 (enquanto escreve
este artigo). Não tem jeito, a versão que acompanha a distro estará sempre desatualizada.

Você deverá compilar os fontes caso queira obter a versão mais atual.

Outra saída bem interessante é o [Phpbrew](http://phpbrew.github.io/phpbrew/), ele te ajudará a
gerenciar diversas versões do PHP, isso é ótimo pois você poderá ter mais de uma versão instalada.
Alias, o Phpbrew é indicado pelo projeto [phptherightway](http://br.phptherightway.com/#instalacao_no_mac).

---


#### Pacotes complementares

Talvez você queira instalar alguns pacotes complementares como, por exemplo a biblioteca GD para
geração de imagens:

    apt-get install php5-gd

Ou a biblioteca __curl__:

    apt-get install php5-curl


Você é quem deve definir o que instalar, para ajudar temos o comando abaixo que lista as possíveis opções...

    apt-cache search php5-

Se precisar de mais informações sobre um pacote específico utilize o seguinte comando.

    apt-cache show package_name

Se você pretende utilizar o PHP com o Apache e já possui ele instalado em sua máquina, então lembre-se de
[reiniciar o Apache](/linux/reiniciar-servidor-apache)

---


### Fedora


Seguimos a mesma idéia de instalação do Ubuntu.

Primeiro instalamos o php:

    yum install php

Depois, os demais pacotes...

    yum install php-common php-pecl-apc php-cli php-pear php-pdo php-mysql php-pgsql php-pecl-mongo
	php-pecl-memcache php-pecl-memcached php-gd php-mbstring php-mcrypt php-xml php-soap


A lista acima era a que eu costumava utilizar, você deve considerar apenas os módulos que você utilizará.

E não se esquece de [reiniciar o Apache ](/linux/reiniciar-servidor-apache) (caso esteja utilizando o Apache).
