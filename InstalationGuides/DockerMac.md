---
layout: default
title: Docker para Mac
parent: Guias de Instalação
nav_order: 6
---

# **Como instalar o Docker no Mac**

![Docker Desktop Logo](../assets/img/Docker/docker-desktop-instalation/docker-desk-banner1.png){: .d-block .mx-auto}

## **Índice**<!-- omit in toc -->

- [**Pré-requisitos**](#pré-requisitos)
- [**Instalação do Docker Desktop**](#instalação-do-docker-desktop)
- [**Verificação**](#verificação)
- [**Observações Finais**](#observações-finais)
- [**Para saber mais**](#para-saber-mais)


## **Pré-requisitos**
Primeiramente, é necessário ter pelo menos 4GB de RAM. Além disso, para usar o Docker Desktop, o macOS deve estar na **versão 10.14 ou mais recente**, ou seja: Mojave, Catalina ou Big Sur.

Ok...mas como eu verifico qual versão do macOS estou? 

Para saber basta ir no canto superior esquerdo da tela, clicar no símbolo da Apple e depois em "Sobre Este Mac". Ali mostrará a versão do Mac que você se encontra!

<img src="../assets/img/Docker/docker-mac-instalation/about-this-mac.png" alt="about-this-mac" height="376" width="428" style ="margin:auto; display:block"> <br />

<img src="../assets/img/Docker/docker-mac-instalation/mac-version.png" alt="mac-version" height="299" width="506" style ="margin:auto; display:block">

## **Instalação do Docker Desktop**

Para instalar o Docker Desktop Installer, basta entrar **[aqui](https://hub.docker.com/editions/community/docker-ce-desktop-mac/)**, e depois clicar em **"Get Docker"**.

<img src="../assets/img/Docker/docker-mac-instalation/download-page.png" alt="download-page" height="295" width="724" style ="margin:auto; display:block">

Feito o download, clique 2 vezes no **Docker.dmg** para abrir o instalador. Aberta a janela, leve o ícone do Docker para a pasta "Applications", conforme a imagem: 

<img src="../assets/img/Docker/docker-mac-instalation/move-app.png" alt="move-app" height="290" width="619" style ="margin:auto; display:block">

Dado o tempo de instalação, clique 2 vezes no ícone do Docker. Talvez poderá aparecer uma janela perguntando se deseja abrir o app baixado da internet. Clique em "Abrir". 

Depois, o Docker pedirá acesso. Clique em "OK" e insira sua senha do Mac para permitir a operação. Por fim, clique em "Instalar Auxiliar".

<img src="../assets/img/Docker/docker-mac-instalation/access-request.png" alt="access-request" height="168" width="529" style ="margin:auto; display:block"> <br />

<img src="../assets/img/Docker/docker-mac-instalation/password.png" alt="password" height="184" width="402" style ="margin:auto; display:block">

**Pronto!** Se tudo estiver certo, abrirá a página inicial do Docker! (sons de aplauso).

<img src="../assets/img/Docker/docker-mac-instalation/start-screen.png" alt="start-screen" height="398" width="632" style ="margin:auto; display:block">

## **Verificação**

Agora vamos verificar se o Docker foi instalado corretamente!

Para isso, abra o Terminal (clique na lupa no canto superior direito e busque "Terminal").

<img src="../assets/img/Docker/docker-mac-instalation/terminal.png" alt="terminal" height="62" width="445" style ="margin:auto; display:block">

Digite a seguinte linha e dê enter:

```bash
docker -v
```
A versão instalada será mostrada, como na figura:

<img src="../assets/img/Docker/docker-mac-instalation/docker-version.png" alt="docker-version" height="48" width="312" style ="margin:auto; display:block">

Além disso, podemos testar se o Docker está funcionando corretamente com o Docker Hub, para testar isso digite no prompt de comando: 

```bash
docker run hello-world
```
<img src="../assets/img/Docker/docker-mac-instalation/hello-world.png" alt="hello-world" height="337" width="583" style ="margin:auto; display:block">

Se a saída for que nem a de cima, está tudo **correto**! (mais sons de aplauso) 

## **Observações Finais**

Se o ícone quando o Docker estiver presente no canto superior direito da tela, significa que ele está ligado.

<img src="../assets/img/Docker/docker-mac-instalation/top-bar.png" alt="top-bar" height="25" width="427" style ="margin:auto; display:block">

Para entrar no Docker Desktop das próximas vezes, basta buscar na lupa ou no Launchpad!

## **Para saber mais**

Para mais informações vejam o **[Manual do Usuário](https://docs.docker.com/docker-for-mac/)** e também o **[guia de instalação oficial do docker](https://docs.docker.com/docker-for-mac/install/)**. 
