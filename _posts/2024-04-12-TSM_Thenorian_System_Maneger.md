---
title: Thex System Server
author: na18k
date: 2024-04-12 10:46:00 +0300
categories: [Na18k, Thenorian, Thex, TSM]
tags: [docs, thex, thenorian, tsm]
---

> Thenorian System Maneger
> Version: v0.0.1-beta

**Thenorian System Maneger**, é um sistema feito em "`Flask 3.0.2`" um módulo "`Python 3`".

## Executando
A execução desse sistema nativamente é pelo Apache 2 dentro de um Ubunto Server.


Confira abaixo os arquivos de ambiente do sistema:
### app.wsgi
##### Caminho: /var/www/folder-project/app.wsgi
```
import sys
sys.path.insert(0, '/var/www/basic-flask-app')

activate_this = '/var/www/env/basic-flask-app-2sD0MLz9/bin/activate_this.py'
with open(activate_this) as file_:
	exec(file_.read(), dict(__file__=activate_this))

from app import app as application
```

### basic-flask-app.conf
##### Caminho: /etc/apache2/sites-available/basic-flask-app.conf
```
<VirtualHost *:80>
    ServerName "IP do sistema"

    WSGIDaemonProcess flaskapp user=www-data group=www-data threads=5
    WSGIScriptAlias / /var/www/basic-flask-app/app.wsgi

    <Directory /var/www/basic-flask-app>
        WSGIProcessGroup flaskapp
        WSGIApplicationGroup %{GLOBAL}
        Order deny,allow
        Allow from all
    </Directory>

    Alias /static /var/www/basic-flask-app/static

    <Directory /var/www/basic-flask-app/static>
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/www/basic-flask-app/logs/error.log
    CustomLog /var/www/basic-flask-app/logs/acess.log combined

</VirtualHost>
```


## Reiniciar Sistema
A execução desse sistema nativamente é pelo Apache 2 dentro de um Ubunto Server.

```

$ sudo /root/restart-system.sh

```
> Esse comando ira reiniciar o Apache 2 e o MySql Server.

### restart-system.sh
##### Caminho: /root/restart-system.sh
```
 #!/bin/bash

# Verifica se o usuário atual tem permissão de sudo
if [ "$(id -u)" != "0" ]; then
    echo "Este script precisa ser executado com permissões de superusuário (root)." 1>&2
    exit 1
fi

# Reinicia o serviço do Apache
sudo systemctl restart apache2.service

# Verifica se o reinício do Apache foi bem-sucedido
if [ $? -eq 0 ]; then
    echo "O serviço Apache foi reiniciado com sucesso."
else
    echo "Ocorreu um erro ao reiniciar o serviço Apache."
fi

# Reinicia o serviço MySQL
sudo systemctl restart mysql.service

# Verifica se o reinício do MySQL foi bem-sucedido
if [ $? -eq 0 ]; then
    echo "O serviço MySQL foi reiniciado com sucesso."
else
    echo "Ocorreu um erro ao reiniciar o serviço MySQL."
fi

```
