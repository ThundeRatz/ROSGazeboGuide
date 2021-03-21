# **Como Instalar o Xserver no Windows**

<br>

Após a instalação do WSl no seu windows, o seu sistema operacional ainda não consegue reproduzir o Gazebo e Rviz.

Por conta disso, nesse tutorial iremos mostrar uma ferramenta que possibilita a a reprodução do Gazebo e Rviz

<br>

---

<br>

## **Índice**

- [**Download e execução do arquivo VcXsrv**](#Download-e-execução-do-arquivo-VcXsrv)
- [**Execução e configuração do Xlaunch**](#Execução-e-configuração-do-Xlaunch)
- [**Após a instalação**](#Após-a-instalação)


<br>

---

<br>

## **Download e execução do arquivo VcXsrv**

<br>

- Baixar o arquivo vcxsrv e salve no seu local de preferencia: 
https://sourceforge.net/projects/vcxsrv/

<br>

![download XServer](../assets/gif/XServer/0_baixando_VcXsrv.gif)

<br>

- Execute o arquivo **"vcxsrv-64.1.20.9.0.installer"**

<br>

![execute o XServer](../assets/gif/XServer/1_executando_VcXsrv.gif)

<br>

## **Execução e configuração do Xlaunch**

<br>

Após baixar e executar o arquivo "vcxsrv-64.1.20.9.0.installer", ele ira criar um arquivo chamado **Xlaunch** na sua area de trabalho (Desktop, se o seu computador estiver em inglês)

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


## **Após a instalação**

<br>

Após isso, está pronta a instalação do Xserver

Depois disso, ***[clique aqui]()***  para executar todo o projeto no seu Windows !
