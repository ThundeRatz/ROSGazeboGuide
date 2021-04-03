---
layout: default
title: Instalando o X server
parent: Guias de Instalação
nav_order: 4
---

![Logo do X server no Windows](../assets/img/logo_Xserver.png)

# **Como Instalar o X server no Windows**

Neste tutorial, vamos aprender a **instalar** o Xorg Server chamado **X server** em sua máquina.
Após a instalação do WSL e ROS, o seu sistema operacional ainda não consegue reproduzir o Gazebo. Por conta disso, nesse tutorial iremos mostrar uma ferramenta que possibilita a reprodução desses programas no Windows.

Não é necessário ter o ROS/Gazebo instalado no seu computador para seguir esse tutorial, mas é necessario o WSL para os toques finais. Dessa forma, recomendo que faça esse tutorial por último.

***[Clique aqui](../InstalationGuides/WSL.md)*** para ser direcionado ao tutorial de instalação do WSL.

***[Clique aqui](../InstalationGuides/ROSGazeboWSL.md)*** para ser direcionado ao tutorial de instalação do ROS/Gazebo.
## **Índice**<!-- omit in toc --> 

- [**Download e execução do arquivo VcXsrv**](#download-e-execução-do-arquivo-vcxsrv)
- [**Execução e configuração do Xlaunch**](#execução-e-configuração-do-xlaunch)
- [**Toques finais**](#toques-finais)
- [**Teste de funcionamento**](#teste-de-funcionamento)
- [**Instruções para pós instalação**](#instruções-para-pós-instalação)

## **Download e execução do arquivo VcXsrv**

- **Baixe** o arquivo **VcXsrv Windows X server** e **salve** no seu local de preferência:

    - ***[Clique aqui](https://sourceforge.net/projects/vcxsrv/)*** para baixar o VcXsrv Windows X server.

![download X server](../assets/gif/XServer/0_baixando_VcXsrv.gif)

- Execute e instale o arquivo **"vcxsrv-64.1.x.x.x.installer"** (obs.: os 'x' estão no lugar da versão, ou seja, desde que estaja dentro da "vcxsrv-64.1", está tudo bem baixar essa opção).
    
    - O arquivo, a priori, já vem com as configurações adequadas, porém, certifique-se que a opção de instalação está "full" e que todas as "caixinhas" estão selecionadas. 
    
![execute o XServer](../assets/gif/XServer/1_executando_VcXsrv.gif)

## **Execução e configuração do Xlaunch**

Após baixar e executar o arquivo "vcxsrv-64.1.x.x.x.installer", ele irá criar um arquivo chamado **Xlaunch** na sua área de trabalho (desktop, se o seu computador estiver em inglês).

Toda vez que computador for reiniciado, esse passo deve ser feito novamente.

- Execute o **Xlaunch**.
- Na aba de configuração de display (select display settings):
    - Deixe **"Multiple windows"** selecionado;
    - Deixe **"display number"** em **0**.

- Na aba de seleção de como iniciar o cliente (select how to start clients):
    - Selecione **"Start no client"**.

- Na aba de configurações extras (extra settings):
    - Deixe selecionado **"Clipboard"**, **"Primary Selection"** e **"Disable acess control"**.

Ao final da instalação, há a opção de salvar as configurações feita, para que não precise refazer os mesmos passos acima toda vez que for iniciar o X server.

- Salvar configurações(opcinal):
    - **Clique** no icone **"Save Configuration"**;
    - **Nomeie** o arquivo como preferir e **salve** no seu local de preferência.

Depois disso, basta clicar no arquivo de configurações salvo para iniciar o X server.

![executando Xlaunch](../assets/gif/XServer/2_executando_Xlaunch.gif)

- Para saber se foi inicializado, certifique-se que existe na extremidade inferior direita o símbolo do Xlaunch.

![Verificação Xlaunch](../assets/img/check_xlaunch.png)

## **Toques finais**

Para conseguir fazer esses toques finais, é necessário ter, pelo menos, o WSL instalado no Windows.

Caso não tenha feito isso ainda, ***[clique aqui](../InstalationGuides/WSL.md)*** para ser direcionado ao tutorial de instalação do WSL.

- Caso esteja usando o **WSL1**, **abra** o **terminal** do Ubuntu no Windows e digite o seguinte comando:

```bash
echo "export DISPLAY=:0" >> ~/.bashrc
source ~/.bashrc
```
Não se preocupe se o terminal não responder nada depois destes comandos -- ele realmente não dá nenhum sinal de que os comandos foram feitos de maneira correta. Na verdade, se não apareceu nada, você provavelmente fez tudo certo.

- Caso esteja usando o WSL2, digite o seguinte no lugar do último comando:

```bash
echo "export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2}'):0" >> ~/.bashrc
source ~/.bashrc
```

## **Teste de funcionamento**
Com todos os passos acima concluidos, você só precisa certificar-se que está tudo funcionando.

- **Abra** o **terminal** do Ubuntu e **Instale** o pacote `mesa-utils` com o seguinte comando:

```bash
sudo apt install mesa-utils
```

![mesa-utils instalation](../assets/gif/XServer/3_mesa_utils_instalation.gif)

- **Digite** no terminal o seguinte comando:

```bash
glxgears
```

Depois desse comando, deve aparecer três engrenagens coloridas girando:

![gears](../assets/gif/XServer/4_gears.gif)

## **Instruções para pós instalação**
Depois disso, está pronta a instalação do X server.

Após a instalação do WSL, ROS/Gazebo e X server, o seu computador está pronto para as experiências que serão realizadas nas aulas!

Bom proveito!

Para aprender a executar seu projeto no Windows, ***[clique aqui](../HowToRun/RunOnWSL.md)***. 
