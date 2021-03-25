![Logo do XServer no windowsa](../assets/img/logo_Xserver.png)

# **Como Instalar o Xserver no Windows**

Neste tutorial, vamos aprender a **instalar** o Xorg Server chamado **Xserver** em sua máquina.


Após a instalação do WSL e ROS, o seu sistema operacional ainda não consegue reproduzir o Gazebo e Rviz. Por conta disso, nesse tutorial iremos mostrar uma ferramenta que possibilita a a reprodução desses programas no seu Windows.

Não é necessário ter o WSL e ROS/Gazebo instalado no seu computador para seguir esse tutorial, porém recomendo que façam esse tutorial por último.

***[Clique aqui](../InstalationGuides/WSL.md)*** para ser direcionado ao tutorial de instalação do WSL 

***[Clique aqui](../InstalationGuides/ROSGazeboWSL.md)*** para ser direcionado ao tutorial de instalação do ROS/Gazebo


## **Índice**<!-- omit in toc --> 

- [**Download e execução do arquivo VcXsrv**](#Download-e-execução-do-arquivo-VcXsrv)
- [**Execução e configuração do Xlaunch**](#Execução-e-configuração-do-Xlaunch)
- [**Instruções para pós instalação**](#Instruções-para-pós-instalação)


## **Download e execução do arquivo VcXsrv**


- **Baixe** o arquivo **VcXsrv Windows X Server** e **salve** no seu local de preferencia:

 ***[clique aqui](https://sourceforge.net/projects/vcxsrv/)*** para baixar o VcXsrv Windows X Server


![download XServer](../assets/gif/XServer/0_baixando_VcXsrv.gif)


- Execute e instale o arquivo **"vcxsrv-64.1.20.9.0.installer"**
    
    - O arquivo, a priori, já vem com as configurações adequadas, porém, certifique-se que a opção de instalação está "full" e que todas as "caixinhas" estão selecionadas. 


![execute o XServer](../assets/gif/XServer/1_executando_VcXsrv.gif)


## **Execução e configuração do Xlaunch**

Após baixar e executar o arquivo "vcxsrv-64.1.20.9.0.installer", ele irá criar um arquivo chamado **Xlaunch** na sua área de trabalho (Desktop, se o seu computador estiver em inglês)

- Execute o **Xlaunch**
- Na aba de configuração de display (select display settings):
    - Deixe **"Multiple windows"** selecionado;
    - Deixe **display number = 0**.

- Na aba de seleção de como iniciar o cliente (select how to start clients):
    - Selecione **"Start no client"**.

- Na aba de configurações extras (extra settings):
    - Deixe selecionado **"Clipboard"**, **"Primary Selection"** e **"Disable acess control"**


![executando Xlaunch](../assets/gif/XServer/2_executando_Xlaunch.gif)



## **Instruções para pós instalação**


Depois disso, está pronta a instalação do Xserver.

Após a instalação do WSL, ROS/Gazebo e Xserver, o seu computador está pronto para as experiências que serão realizadas nas aulas!

Bom proveito!

Para aprender a executar seu projeto no Windows, ***[clique aqui](ProjectExecutationGuide/RunOnWSL.md)*** 

