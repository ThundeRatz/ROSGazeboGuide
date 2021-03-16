# Instalando o ROS/Gazebo em sua máquina

## **Como Instalar ROS/Gazebo em Ubuntu**
--------------------------

Neste tutorial, vamos aprender como instalar ROS/Gazebo no Ubuntu.

Grande parte do tutorial vai utilizar o prompt de comando -- então abre ele aí! O formato para escrever um comando será o seguinte:
```
comando-a-inserir
```
Então, toda caixinha que você encontrar nesse formato, saiba que é um comando a ser inserido.

### **Habilitando Repositórios**
--------------------------

Primeiramente, para instalar ROS em Ubuntu, precisamos configurar os **repositórios Ubuntu** para permitir *"restricted", "universe", e "multiverse"*. Podemos fazer isso com os seguintes comandos:

```
sudo add-apt-repository restricted
sudo add-apt-repository universe
sudo add-apt-repository multiverse
sudo apt update
```
Esses comandos permitem com que o seu comando **apt** consiga baixar arquivos de fontes mais "alternativas". Existem os programas canônicos que podem ser baixados do repositório **main**, mas para a instalação do ROS, precisamos habilitar os repositórios **universe** (software de graça e Open Source para qual o Ubuntu não fornece atualizações de segurança), **multiverse** (que contém software que não é de graça ou Open Source ~~mas baixamos mesmo assim~~) e **restricted** (que contém drivers com proprietários).

Em suma, utilizamos este comando para que o Ubuntu tenha as permissões corretas para instalar o que queremos.

### **Ajustar a sources.list**
--------------------------
Vamos agora ajustar o computador para aceitar software da **packages.ros.org** :

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

### **Ajustar as keys**
--------------------------
Insira o seguinte comando para "setar" as keys para a instalação:
```
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```
Se você tiver problemas se conectando com o keyserver, você pode tentar usar o seguinte comando:

```
sudo apt-key adv --keyserver 'hkp://pgp.mit.edu:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```
Alternativamente, você pode utilizar o comando *"curl"*, que pode ser útil se você estiver em um servidor proxy:

```
curl -sSL 'http://keyserver.ubuntu.com/pks/lookup?op=get&search=0xC1CF6E31E6BADE8868B172B4F42ED6FBAB17C654' | sudo apt-key add -
```

### **Finalmente, a instalação!**
--------------------------

Primeiro, vamos dar um update para "lavar as mãos" e ter certeza que está tudo atualizado:
```
sudo apt update
```
Feito isso, vamos instalar o pacote do ROS. **Precisamos** instalar o pacote **"desktop-full"** para instalar os adendos responsáveis por simulação 2D/3D -- como o *Gazebo* -- senão faltará coisas na máquina. Assim, o comando é:

```
sudo apt install ros-noetic-desktop-full
```
Este comando deve instalar o ROS e o Gazebo juntos. Podemos também instalar pacotes específicos diretamente por meio do seguinte comando:
```
sudo apt install ros-noetic-PACKAGE
```
Sendo PACKAGE o nome do pacote a ser instalado -- mas isso não será necessário por enquanto.

### **Preparando o "Ambiente"**
--------------------------
É importante que você defina a "source" deste script em todo terminal **bash** que você usa ROS.
```
source /opt/ros/noetic/setup.bash
```

Você também pode ajustar para que o "source" deste script seja definido sempre que um novo prompt de comando *shell* for inicializado. Estes comandos fazem isso:

- Bash
```
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
- zsh
```
echo "source /opt/ros/noetic/setup.zsh" >> ~/.zshrc
source ~/.zshrc
```
# Como Instalar ROS/Gazebo em WSL
Os passos da instalação do ROS/Gazebo são similares ao ubuntu sem o WSL

<div>Abra o terminal do Ubuntu no Windows</div>
<div align=center>
<img src="https://lh3.googleusercontent.com/pw/ACtC-3d1hybWo5Ee3nwj01Vk_NElno6nyDpEgMNFz5WN_AKVfxd_6ImQZFt4iVdGHDOqAvFGOQa5KpMoMO7OlKEuW5_51D-NsbIa9r_A-7UrBLxv5U_KuDJfhrUizCOUk6cqAr5Ve1U6P07r775GQOqHjY0=w1356-h721-no?authuser=3" width="750" height="400" />
</div>

### **Habilitando Repositórios**
--------------------------

Primeiramente, para instalar ROS no Ubuntu em WSL, precisamos configurar os **repositórios Ubuntu** para permitir *"restricted", "universe", e "multiverse"*. Podemos fazer isso com os seguintes comandos:

```
sudo add-apt-repository restricted
sudo add-apt-repository universe
sudo add-apt-repository multiverse
sudo apt update
```
**Resposta esperada:**
<div align=center>
<img src="https://lh3.googleusercontent.com/pw/ACtC-3eZ6NukBBtIowC7i3GozbB45l7A6W3OEBRCKAUyi652BCPmzy1EQHjQk9hxic5hOqVicQQ7H0apqETjlaNAYgMEP7QN7hLtWxXwMXUaino2igWRGRMcsMqUpM837J0v-fchMDr8y9cuyoXfrmUepBE=w1274-h669-no?authuser=3" width="700" height="350" />
</div>


Esses comandos permitem com que o seu comando **apt** consiga baixar arquivos de fontes mais "alternativas". Existem os programas canônicos que podem ser baixados do repositório **main**, mas para a instalação do ROS, precisamos habilitar os repositórios **universe** (software de graça e Open Source para qual o Ubuntu não fornece atualizações de segurança), **multiverse** (que contém software que não é de graça ou Open Source ~~mas baixamos mesmo assim~~) e **restricted** (que contém drivers com proprietários).

### **Ajustar a sources.list**
--------------------------
Vamos agora ajustar o computador para aceitar software da **packages.ros.org** :

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

### **Ajustar as keys**
--------------------------
Insira o seguinte comando para "setar" as keys para a instalação:
```
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```
Se você tiver problemas se conectando com o keyserver, você pode tentar usar o seguinte comando:

```
sudo apt-key adv --keyserver 'hkp://pgp.mit.edu:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```
Alternativamente, você pode utilizar o comando *"curl"*, que pode ser útil se você estiver em um servidor proxy:

```
curl -sSL 'http://keyserver.ubuntu.com/pks/lookup?op=get&search=0xC1CF6E31E6BADE8868B172B4F42ED6FBAB17C654' | sudo apt-key add -
```

**Respostas esperadas:**
<div align=center>
<img src="https://lh3.googleusercontent.com/pw/ACtC-3c9t5J72-TA8wMdalRwG8_dlZXjazpImfgRrIMRPcGcvO7q7jOpNq1OWrlEp81ZxzNKdQ4xDbuNrVmbJd2C-LE22jtvL2YGq0KnUUkFy5toZuLTBJoTkn-Hc7C7JmCshY5S3ZEemgo3FgAsnBZPZjk=w1274-h669-no?authuser=3" width="700" height="350" />
</div>

### **Finalmente, a instalação!**
--------------------------

Primeiro, vamos dar um update para ter certeza que está tudo atualizado:
```
sudo apt update
```
Feito isso, vamos instalar o pacote do ROS. **Precisamos** instalar o pacote **"desktop-full"** para instalar os adendos responsáveis por simulação 2D/3D -- como o *Gazebo* -- senão faltará coisas na máquina. Assim, o comando é:

```
sudo apt install ros-noetic-desktop-full
```
Este comando deve instalar o ROS e o Gazebo juntos. Podemos também instalar pacotes específicos diretamente por meio do seguinte comando:
```
sudo apt install ros-noetic-PACKAGE
```
Sendo PACKAGE o nome do pacote a ser instalado -- mas isso não será necessário por enquanto.

**Resposta esperada:**
<div align=center>
<img src="https://lh3.googleusercontent.com/pw/ACtC-3cQGWtcaenWvIRceiKe-Uc7R13U7ddaY5XdX2Z9bOMIgYeAZyJsqakBU-iEhuaPwJg_7kZw4kC-VNEAymBxAg5ZfHnUZ0BPcmvBuN6lUTG7LDTRhx648jA1YHnxMGcYWJYszd7kX-S1uE_Hd3pCQm4=w1274-h669-no?authuser=3" width="700" height="350" />
</div>

### **Preparando o "Ambiente"**
--------------------------
É importante que você defina a "source" deste script em todo terminal **bash** que você usa ROS.
```
source /opt/ros/noetic/setup.bash
```

Você também pode ajustar para que o "source" deste script seja definido sempre que um novo prompt de comando *shell* for inicializado. Estes comandos fazem isso:

- Bash
```
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
- zsh
```
echo "source /opt/ros/noetic/setup.zsh" >> ~/.zshrc
source ~/.zshrc
```
**Resposta esperada:**
<div align=center>
<img src="https://lh3.googleusercontent.com/pw/ACtC-3exhm3PDyOBMMDRGpJpPhkTam21f_Qe9DscdEdtNZNoVgzVGqDTC7j8R80AhRnG9U17PQLvuVB5JeGGil7l7VOLl8LxhMEIUqetVZBKTzjn31fmdQpm9rLukMBo1YUzFVqrd_BIUipvGupIYd0iCcI=w1276-h672-no?authuser=3" width="700" height="350" />
</div>

## Como rodar Gazebo + RVIZ e Windows 10 usando WSL2
Após a instalação, é necessario instalar uma extensão para reproduzir o Gazebo e Rviz
- Baixar:
https://sourceforge.net/projects/vcxsrv/

Após baixar a exetensão

- Execute o Xlaunch
Na aba de configuração de display(select display settings):
- Deixe "Multiple windows" selecionado
- Deixe display number = 0
Na aba de seleção de como iniciar o cliente(select how to start clients):
- Selecione "Start no client"
Na aba de configurações extras(extra settings):
- Deixe selecionado "Clipboard", "Primary Selection" e "Disable acess control"
Após isso é só finalizar a configuração

- Digite no terminal do ubuntu do WSL:
```
export GAZEBO_IP=127.0.0.1
export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2}'):0 
export LIBGL_ALWAYS_INDIRECT=0
```
Depois disso, toda vez que o gazebo for executado no ubuntu, uma aba será aberta automaticamente
 

<div>Para mais informações siga o tutorial no seguinte vídeo:</div>
<a href="http://www.youtube.com/watch?feature=player_embedded&v=DW7l9LHdK5c
" target="_blank"><img src="http://img.youtube.com/vi/DW7l9LHdK5c/0.jpg" 
alt="link vídeo" width="240" height="180" border="10" /></a>







 