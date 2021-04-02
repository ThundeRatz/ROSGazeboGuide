---
layout: default
title: ROS/Gazebo no WSL
parent: Guias de Instalação
nav_order: 2
---


# **Instalando o ROS/Gazebo em sua máquina com o WSL**

Neste tutorial, vamos aprender a **instalar** o framework chamado **ROS** em sua máquina. Junto com ele, vem o simulador **Gazebo**, que permite com que você faça o seu robôzinho andar por aí.
Se quiser aprender mais e entender para que servem ROS e Gazebo, veja os documentos explicativos (o que é? / porque usar?) sobre cada um deles - com certeza vai iluminar melhor a questão.

Neste documento, vamos dar um enfoque a como instalar ROS/Gazebo no Windows com WSL.

### **Se você está utilizando Ubuntu, você está lendo o artigo errado. ***[Clique aqui](../InstalationGuides/ROSGazeboUbuntu.md)*** para se redirecionar.**

## **Índice**<!-- omit in toc -->

- [**O que vamos usar?**](#o-que-vamos-usar)
- [**Habilitando Repositórios**](#habilitando-repositórios)
- [**Ajustar a sources.list**](#ajustar-a-sourceslist)
- [**Ajustar as chaves**](#ajustar-as-chaves)
- [**Finalmente, a instalação!**](#finalmente-a-instalação)
- [**Toques finais**](#toques-finais)
- [***Instruções para pós instalação***](#instruções-para-pós-instalação)


## **O que vamos usar?**

Os passos da instalação do ROS/Gazebo são similares ao Ubuntu sem o WSL:

Abra o **terminal** do Ubuntu no Windows

![abertura ubuntu](../assets/gif/ROSGazebo/WSL/0_opening_ubuntu.gif)

Após abrir o terminal, você poderá inserir comandos que vão realizar tarefas para você. É a maneira principal de se instalar pacotes no Ubuntu do WSL.

Utilizaremos esses comandos como ferramenta principal para a instalação deste framework.
O formato para escrever um comando será o seguinte:
```bash
comando-a-inserir
```
Então, toda caixinha que você encontrar nesse formato, saiba que é um comando a ser inserido.

Após inserir um comando é esperado que ele responda com algumas saídas. Assim, para o comando:

```bash
ls
```
O terminal responderá da seguinte forma, apresentando os arquivos e pastas da pasta que você se encontra:

![comando ls](../assets/gif/ROSGazebo/WSL/command_ls.gif)

## **Habilitando Repositórios**

Primeiramente, para instalar ROS no Ubuntu do WSL, precisamos configurar os **repositórios Ubuntu** para habilitar os repositórios *"restricted", "universe", e "multiverse"*.

Mas o que é um repositório?

Sucintamente, um repositório é um **servidor** que contém diversos **pacotes**, isto é, arquivos e programas, que estão disponibilizados para usuários instalarem em suas máquinas. Por padrão, o Ubuntu não habilita o acesso aos repositórios restricted, universe e multiverse -- mas para instalar o ROS precisamos de acesso a esses servidores.

Podemos habilitar o acesso com os seguintes comandos:

``` bash
sudo add-apt-repository restricted
sudo add-apt-repository universe
sudo add-apt-repository multiverse
sudo apt update
```
A resposta esperada desse comando é a seguinte:

![configurando repositório](../assets/gif/ROSGazebo/WSL/1_repositories.gif)

Esses comandos permitem com que a sua máquina obtenha arquivos de diferentes tipos de repositório.

Para saber mais sobre as diferenças entre cada repositório, acesse o link:
<https://help.ubuntu.com/community/Repositories>

Em seguida, vamos configurar algumas coisas para que a sua máquina consiga buscar e aceitar o arquivo do servidor fornecedor.

## **Ajustar a sources.list**

Vamos agora ajustar o computador para aceitar pacotes do **repositório do ROS** :

```bash
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
Não se preocupe se o terminal não responder nada depois deste comando -- ele realmente não dá nenhum sinal de que o comando foi feito de maneira correta. Na verdade, se não apareceu nada, você provavelmente fez tudo certo.

## **Ajustar as chaves**

Insira o seguinte comando para salvar as chaves do repositório do ROS na sua máquina:

```bash
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```

A resposta esperada desses comandos é a seguinte:

![configurando key e source](../assets/gif/ROSGazebo/WSL/2_source_key.gif)

As chaves são necessárias para acesso ao repositório do ROS, do qual instalaremos nossos arquivos. Se você não fizer esta parte, não terá acesso a ele e não conseguirá instalar.

## **Finalmente, a instalação!**

Primeiro, vamos rodar um comando para atualizar o sistema com as modificações que fizemos até agora:

```bash
sudo apt update
```
Feito isso, vamos instalar o pacote do ROS. **Precisamos** instalar o pacote **"desktop-full"** para instalar os adendos responsáveis por simulação 2D/3D -- como o *Gazebo* -- senão faltarão pacotes na máquina. Assim, o comando é:

```bash
sudo apt install ros-noetic-desktop-full
```

Este comando deve instalar o ROS e o Gazebo juntos.

A resposta esperada desses comandos é a seguinte:

![instalação](../assets/gif/ROSGazebo/WSL/3_instalation.gif)

Note que, no meio da execução, o terminal pergunta **"Do you want to continue? [Y/n]"**.
Para continuar, basta escrever **y** e apertar Enter.
Neste caso também, se você não escrever nada e somente pressionar Enter, a resposta default é "Yes", então você também pode fazer isso.

Ao final da execução, tudo deve ter sido instalado da maneira correta. Para testar, vamos utilizar o comando a seguir:

```bash
gazebo -version
```

A resposta esperada desse comando é a seguinte:

![verificando versão do gazebo](../assets/gif/ROSGazebo/WSL/gazebo_version.gif)

Tendo feito tudo isso, podemos também instalar pacotes específicos diretamente por meio do seguinte comando:
```bash
sudo apt install ros-noetic-PACKAGE
```
Sendo PACKAGE o nome do pacote a ser instalado -- mas isso não será necessário por enquanto.


## **Toques finais**

Toda vez que você abrir um terminal, é necessário executar o seguinte comando para habilitar o ambiente ROS na sua sessão de terminal:

```bash
source /opt/ros/noetic/setup.bash
```

Rodar esse comando manualmente sempre pode se tornar trabalhoso. Para facilitar o nosso trabalho, configuramos o sistema para fazer isso automaticamente.

A maneira de fazer isso é a seguinte:

```bash
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

O que esse comando faz é adicionar a linha de texto `source /opt/ros/noetic/setup.bash` para o arquivo `.bashrc`. Este arquivo contém uma lista de comandos que são executados toda vez que um novo terminal é aberto. Dessa forma, você não precisa escrever o mesmo comando sempre.

## ***Instruções para pós instalação***

Após estes toques finais, a instalação do ROS e do Gazebo estará finalizada!

Mas vamos com calma ainda, amigo. Para utilizar o ROS e suas extensões pelo WSL será necessário instalar o Xserver, para o qual também temos um guia de instalação!

Para instalar o Xserver  ***[clique aqui](../InstalationGuides/XServer.md)***

Depois disso tudo isso, seu Windows estará pronto para utilizar corretamente o ROS.

Bom proveito!
