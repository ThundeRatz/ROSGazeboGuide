![Logo do XServer no windowsa](../assets/img/logo_Xserver.png)

<br>

# **Como Instalar o Xserver no Windows**

Neste tutorial, vamos aprender a **instalar** o Xorg Server chamado **Xserver** em sua máquina.
Após a instalação do WSl e ROS, o seu sistema operacional ainda não consegue reproduzir o Gazebo e Rviz.

Por conta disso, nesse tutorial iremos mostrar uma ferramenta que possibilita a a reprodução do Gazebo e Rviz.

Não é necessário ter o WSL e ROS/Gazebo instalado no seu computador para seguir esse tutorial, porém recomendo que façam esse tutorial por último.

***[Clique aqui](../InstalationGuides/WSL.md)*** para e direcionar para o tutorial de instalação do WSL 

***[Clique aqui](../InstalationGuides/ROSGazeboWSL.md)*** para e direcionar para o tutorial de instalação do ROS/Gazebo


## **Índice**
- [**Índice**](#Índice)
- [**Download e execução do arquivo VcXsrv**](#Download-e-execução-do-arquivo-VcXsrv)
- [**Execução e configuração do Xlaunch**](#Execução-e-configuração-do-Xlaunch)
- [**Instruções para pós instalação**](#Instruções-para-pós-instalação)


<br>

## **Download e execução do arquivo VcXsrv**

<br>

- **Baixe** o arquivo **VcXsrv** e **salve** no seu local de preferencia:

Para baixar o VcXsrv ***[clique aqui](https://sourceforge.net/projects/vcxsrv/)***

<br>

![download XServer](../assets/gif/XServer/0_baixando_VcXsrv.gif)

<br>

- Execute e instale o arquivo **"vcxsrv-64.1.20.9.0.installer"**
    
    - Deixe a opção de instalação em "full" e todas as "caixinhas" selecionadas. 

<br>

![execute o XServer](../assets/gif/XServer/1_executando_VcXsrv.gif)

<br>

## **Execução e configuração do Xlaunch**

<br>

Após baixar e executar o arquivo "vcxsrv-64.1.20.9.0.installer", ele irá criar um arquivo chamado **Xlaunch** na sua área de trabalho (Desktop, se o seu computador estiver em inglês)

- Execute o **Xlaunch**
- Na aba de configuração de display(select display settings):
    - Deixe **"Multiple windows"** selecionado;
    - Deixe **display number = 0**.

- Na aba de seleção de como iniciar o cliente(select how to start clients):
    - Selecione **"Start no client"**.

- Na aba de configurações extras(extra settings):
    - Deixe selecionado **"Clipboard"**, **"Primary Selection"** e **"Disable acess control"**

<br>

![executando Xlaunch](../assets/gif/XServer/2_executando_Xlaunch.gif)

<br>


## **Instruções para pós instalação**

<br>

Depois disso, está pronta a instalação do Xserver.

Após a instalação do WSL, ROS/Gazebo e Xserver, o seu computador está pronto para as experiencias que serão realizadas nas aulas!

 ***[clique aqui]()***  para executar todo o projeto no seu Windows!
