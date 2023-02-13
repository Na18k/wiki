---
title: Thex System Server
author: na18k
date: 2023-02-13 14:09:00 +0300
categories: [Na18k, Wiki, Thex]
tags: [config, thex]
---

> Thex System Server
> Version: v0.0.1-beta

**Thex System Server**, é um sistema que hospeda um pasta diretamente do seu computador para WEB, utilizando Python nativo e o modulo `http.server`, disponibilizando um pasta para que seja acessada pelo IP da maquina host.

## Executando
Para executar o Thex System Server, basta baixar o .ZIP disponibilizado [aqui](https://github.com/Thex1223/ThexSystemServer/raw/main/dist/Thex_System_Server.zip).

Basta executar o `TSS.exe`, ele abri-rá um tela de console.

> A janela de console não aceita entradas!

Assim que executar, o sistema irá ter sua configuração padrão, sendo o IP da maquina na qual está sendo executada, e PORTA padrão do sistema, que é `25565` (porta pouca convencional).

Caso queira configurações personalizadas, veja a secção de **Configuração**.

## Finalizar o sistema
Para finalizar o sistema é apenas necessário se fechar a janela de console.
> Cuidado, se algo estiver sendo executado entre o cliente e o host, essa ação pode ser perdida, certifique-se que ocorreu conforma planejado antes de fechar

## Configuração 
*Para uso de configurações personalizadas.*

Para configurar o sistema basta editar o arquivo "`data.json`", na qual se encontra na pasta raiz.

Em `data.json` é possível configurar **endereço ip**, **porta**, **diretório**, e as **mensagens** do programa.

### data.json
    {  
       "config": true,  
       "ip": "",  
       "port": 25565,  
       "diretory": "./data",  
       "msg": {  
          "1": "[INICIANDO WEB SERVER]",  
          "2": "Esse Web Server está configurado...",  
          "3": "Configurado em 'data.json'",  
          "4": "Certifique que está tudo em ordem nas configurações!",  
          "5": "Caso queira você pode editar o arquivo 'data.json', e suas configurações...",  
          "6": "Certifique que está tudo em ordem nas configurações!"  
      }  
    }

Essa configuração e a padrão que já vem junto ao sistema.

### "config"
Caso queira, usar configurações personalizadas, é necessário atualizar a configuração "`config`" para `true`, se não a configuração dentro do próprio sistema será usada.

Deve-se deixar assim: `"config": true`

### "ip"

O ip vem por padrão um string vazia, e pode ser colocado o ip da maquina caso queira.

Caso for deixado da forma que está (`"ip": ""`), o próprio sistema irá obter o IP da maquina, usando esse IP como padrão.

> Deve-se lembrar que ao inserir o IP, deve ser dentro de um string, utilizando o formato abaixo:
> Ex: `"192.168.0.0"`

### "port"

A porta vem como padrão em todo sistema `25565`.
> Esse número de porta foi escolhido por ser menos usual, e acabando não interferindo em outras portas que a maquina ao executar tenha aberta já.

É possível editar a porta apenas substituindo o conteúdo da mesma.

> Deve-se lembrar que nessa configuração dever ser um número inteiro, e de preferencia que seja no mínimo 4 números, e no máximo 5 números.

> Ex 1: `"port": 0000`
> Ex 2: `"port": 00000`


### "diretory"
O diretório ou pasta, é colocada aqui, por padrão ela vem como `"./data"`, que acessa diretamente um pasta que veem junto ao programa.

É possível editar essa pasta de destino a ser compartilhada, editando essa configuração.

> Lembrando que deve ser de preferencia uma pasta.

É possível hospedar um `.html`, se houver um `index.html`, dentro desta pasta ou outros formatos, mais sendo em si `.html`, é mostrado automaticamente, o html funcionando.

> Deve-se seguir o formato a seguir:
> Ex: "diretory": "./data"

### "msg"
Essa configuração é um configuração de estilo, sendo algo não influenciado ao sistema, sendo principalmente estético.

É possível traduzir para que as mensagens sejam visualizadas na língua de preferencia.

> Não retire a opção `"msg"` do arquivo `data.json`, o programa pode apresentar falhas!

> Não é possível editar todas as mensagens, já que é utilizado o modulo `http.server` e o mesmo apresenta mensagens próprias no idioma Inglês.
