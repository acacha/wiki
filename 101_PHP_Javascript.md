# Clase 101. Preparar sistema Ubuntu 20.04 acabat instal·lar per treballar amb PHP, composer, Laravel i Javascript/Nodejs amb PhpStorm

[![Alt text](https://img.youtube.com/vi/w8j07_DBl_I/0.jpg)](https://www.youtube.com/watch?v=w8j07_DBl_I)

Vegeu el videotutorial a: 
- https://youtu.be/w8j07_DBl_I

# Recursos
- https://github.com/2DAM-2020-21/sergitur/blob/master/101_21_09_2020.md
- http://acacha.org/mediawiki/Upgrade
-
# Llista de tasques realitzades

- [ ] Actualització del sistema amb sudo apt-get update && sudo apt-get dist-upgrade
- [ ] Instal·lació de Chrome
- [ ] Instal·lació eines bàsiques línia comandes: joe, nmap, curl http://acacha.org/mediawiki/Upgrade
- [ ] Instal·lació git
- [ ] Instal·ació shell Z i comanda Z
- [ ] Instal·lació de gestors de paquets Composer (PHP) i npm/Yarn (Javascript). Opcional: Creació de compte a https://packagist.org/ i a https://www.npmjs.com/.
- [ ] Comprendre com funciona PATH a Linux i fitxers rc: ~/.bashrc i ~/.zshrc (https://rootsudo.wordpress.com/2014/04/06/el-path-la-ruta-de-linux-variables-de-entorno/)
- [ ] Instal·lació de Laravel. Documentació extra: https://laravel.com/docs/8.x/installation
- [ ] Creació de la carpeta ~/Code. Creació de la carpeta ~/Code/USUARI_GITHUB on posareu tot el codi
- [ ] Instal·lació i configuració de Laravel valet
- [ ] Configuració i instal·lació de Node JS

# Tasques opcionals

- [ ] Instal·lació Android Studio i configuració
- [ ] Instal·lació Ionic
- [ ] Instal·lació Vue
- [ ] Altres: Redis, http-server, supervisor, gh i git-open



# Comandes

IMPORTANT:

Sistema:

 $ sudo apt-get update && sudo apt-get dist-upgrade

Altres software manual
:*Baixar Chrome per Debian i instal·lar: https://www.google.com/intl/es_ALL/chrome/
:*Configurar Compte Google Chrome per a instal·lar tots els plugins
:*Baixar PhpStorm i Android Studio
:*Optional: Instal·lar els code editors (Visual Studio Code, sublime)

Git, curl i altres:

 $ sudo apt-get install git curl joe arandr autossh


Z i zshell:

 $ sudo apt-get install zsh
 $ chsh --shell /usr/bin/zsh sergi

oh my zsh:

 $ sudo apt-get install curl
 $ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

Z:

 $ wget https://raw.githubusercontent.com/rupa/z/master/z.sh

Afegir a .bashrc i .zshrc:

 # include Z, yo
 . ~/z.sh

Finalment alguns alias i funciones també poden ser interessants a afegir als fitxers rc:

<pre>
alias nah="git reset --hard;git clean -df;"

co() {
  git status
  git add .
  git commit -a -m "Sync"
  git pull origin master
  git push origin master
  git status
}
</pre>


PHP:

 $ sudo apt-get install  php7.3-cli

Composer (codi extret de https://getcomposer.org/download/):

 cd
 php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
 php -r "if (hash_file('SHA384', 'composer-setup.php') === '669656bab3166a7aff8a7506b8cb2d1c292f042046c5a994c43155c0be6190fa0355160742ab2e1c88d40d5be660b410') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
 php composer-setup.php
 php -r "unlink('composer-setup.php');"

I ara fem composer disponible a tot el sistema:

 $ sudo cp ~/composer.phar /usr/bin/composer
 $ sudo mv ~/composer.phar /usr/local/bin/composer

Consulteu on teniu la carpeta Global de composer:

 $ composer config --list --global | grep home

I actualitzeu ~/.bashrc i ./zshrc:

 export PATH=${PATH}:~/.composer/vendor/bin
 export PATH=${PATH}:~/.config/composer/vendor/bin

PHPUnit:

 $ composer global require "phpunit/phpunit"

Laravel:

 $ composer global require "laravel/installer"
 $  sudo apt-get install php7.3-mbstring php7.3-zip php7.3-xml php7.3-sqlite3 php7.3-mysql php-curl php7.3-gd php-redis php7.3-gmp php7.3-ldap php7.3-imagick
 
Laravel valet:

 $ sudo apt-get install network-manager libnss3-tools jq xsel

Afegiu al fitxer .zshrc la següent funció de shell:

<pre class="brush:bash">
adminlte() {
    cd ~/Code
    laravel new $1
    cd $1
    adminlte-laravel install
    llum boot
    yarn
    pstorm .
    llum github:init
}
</pre>

Java: (vegeu [[Java_Sun#Instal.C2.B7laci.C3.B3_2]])

Node.js:

 Aneu a https://nodejs.org/es/download/

I baixeu binaries Linux per 64 bits:

  $ mv ~/Baixades/node-v6.10.2-linux-x64.tar.xz  ~
 $ cd 
 $  tar xvf node-v6.10.2-linux-x64.tar.xz 

Configureu ~/.bashrc i ~/.zshrc:

 export PATH=${PATH}:~/node-v6.10.2-linux-x64/bin

Ionic/Cordova/Phonegap:

 $ npm install -g cordova ionic gulp

Yarn:

 $ npm -g install yarn

Http-server:

 $ npm -g install http-server

Nvidia:

 $ ubuntu-drivers autoinstall

Android Studio:

 $ sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0 lib32stdc++6

Vue-cli:

 $ npm install -g @vue/cli

Per evitar errors limi watchers:

 $ echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p

Dependència per a Testing amb cypress:

 $ sudo apt-get install libgconf2-4

Other npm globals:

 $ npm install --global gulp http-server git-open

Altres paquets:

 $ sudo apt-get install nmap wireshark traceroute whois wine

 $ sudo apt-get install traceroute nmap whois wireshark

Redis:

 $ sudo apt-get install redis-server

Supervisor:

 $ sudo apt-get install supervisor

Claus SSH i Github:

Seguiu les passes de:

 https://help.github.com/articles/connecting-to-github-with-ssh/



