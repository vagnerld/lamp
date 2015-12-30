

# Instalação LAMP
### No ubuntu
Pilha Lamp:

* **L**inux (ubuntu 14.04)
* **A**pache
* **M**ySQL
* **P**HP

## Instalação:

### Instalar o Apache:

```sh
sudo apt-get update
sudo apt-get install apache2
```
(verificar http://localhost para saber se o apache foi instalado com sucesso)

### Instalar o MySQL: 
```sh
sudo apt-get install mysql-server php5-mysql
```
Durante a instalação, seu servidor vai pedir para você selecionar e confirmar uma senha para o usuário "root" do MySQL. Esta é uma conta administrativa no MySQL que possui privilégios avançados.

precisamos dizer ao MySQL para criar sua estrutura de diretório de banco de dados, onde ele irá armazenar suas informações. Você pode fazer isto digitando:
```sh
sudo mysql_install_db
```

Depois, queremos executar um script simples de segurança que vai remover alguns padrões perigosos e bloquear um pouco o acesso ao nosso sistema de banco de dados. Inicie o script interativo executando:
```sh
sudo mysql_secure_installation
```

### Instalar o PHP:
```sh
sudo apt-get install php5 libapache2-mod-php5 php5-mcrypt
```

Colocar o arquivo **index.php** sendo prioritário no apache:
```sh
sudo nano /etc/apache2/mods-enabled/dir.conf
```
Colocar index.php no início:
```sh
<IfModule mod_dir.c>
    DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
```

Restartar o servidor apache:
```sh
sudo service apache2 restart
```

### Testar o processamento PHP no seu servidor web

A fim de testar se nosso sistema está corretamente configurado para o PHP, podemos criar um script bem básico.

Vamos chamar este script de info.php. Para que o Apache possa encontrar o arquivo e servi-lo corretamente, ele deve ser salvo em um diretório muito específico, o qual é chamado de "web root".

No Ubuntu 14.04, este diretório está localizado em /var/www/html. Podemos criar o arquivo neste local digitando:
```sh
sudo nano /var/www/html/info.php
```
Isto vai abrir um arquivo em branco. Queremos colocar o texto a seguir, que é um código PHP válido, dentro do arquivo:
```sh
<?php
    phpinfo();
?>
```

O endereço que você quer visitar será: http://localhost/info.php

A página que você deve ver deve se parecer com isto:
<img src="https://assets.digitalocean.com/articles/lamp_1404/default_php.png">

** Seu servidor LAMP foi instalado com sucesso! **

