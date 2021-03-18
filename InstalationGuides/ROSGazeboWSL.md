# Instalando o ROS/Gazebo em sua máquina

Neste tutorial, vamos aprender a **instalar** o software chamado **ROS** em sua máquina. Junto com ele, vem o ambiente de simulação **Gazebo**, que permite com que você faça o seu robôzinho andar por aí.
Se quiser aprender mais sobre os softwares e para que servem, veja os documentos explicativos (o que é? / porque usar?) sobre cada software - com certeza vai iluminar melhor a questão.

Vamos, neste documento, dar um enfoque a como instalar ROS/Gazebo no Windows com WSL.

Se você está utilizando Ubuntu, você está lendo o artigo errado. [Clique aqui](/InstalationGuides/ROSGazeboUbuntu) para se redirecionar.

## Índice
---

- [**Habilitando Repositórios**](#habilitando-repositórios)
- [**Ajustar a sources.list**](#ajustar-a-sources.list)
- [**Ajustar as keys**](#ajustar-as-keys)
- [**Finalmente, a instalação!**](#finalmente-a-instalação!)
- [**Preparando o "Ambiente"**](#preparando-o-"ambiente")
- [**Como rodar Gazebo + RVIZ e Windows 10 usando WSL2**](#como-rodar-gazebo-+-rviz-e-windows-10-usando-wsl2)

---

## **Como Instalar ROS/Gazebo em WSL**
Os passos da instalação do ROS/Gazebo são similares ao Ubuntu sem o WSL:

<div>Abra o terminal do Ubuntu no Windows</div>
<div align=center>
<br>

<img src="https://lh3.googleusercontent.com/pw/ACtC-3d1hybWo5Ee3nwj01Vk_NElno6nyDpEgMNFz5WN_AKVfxd_6ImQZFt4iVdGHDOqAvFGOQa5KpMoMO7OlKEuW5_51D-NsbIa9r_A-7UrBLxv5U_KuDJfhrUizCOUk6cqAr5Ve1U6P07r775GQOqHjY0=w1356-h721-no?authuser=3" width="900" height="450" />
</div>
<br>

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
<img src="https://lh3.googleusercontent.com/pw/ACtC-3eZ6NukBBtIowC7i3GozbB45l7A6W3OEBRCKAUyi652BCPmzy1EQHjQk9hxic5hOqVicQQ7H0apqETjlaNAYgMEP7QN7hLtWxXwMXUaino2igWRGRMcsMqUpM837J0v-fchMDr8y9cuyoXfrmUepBE=w1274-h669-no?authuser=3" width="800" height="400" />
</div>

<br>

Esses comandos permitem com que o seu comando **apt** consiga baixar arquivos de fontes alternativas. Isto é, você permite que sua máquina retire arquivos de repositórios que não recebem suporte da plataforma. Uma tabela que explicita melhor a diferença entre cada tipo de repositório é a seguinte:

-                       | Software Grátis   | Software Não Grátis
-                       |         -         | -
**Recebe Suporte**      | Main              | Restricted
**Não Recebe Suporte**  | Universe          | Multiverse

<br>

Em suma, utilizamos este comando para que o Ubuntu se permita instalar arquivos de repositórios de diversos tipos, de graça ou não, que recebem suporte ou não.

Em seguida, vamos configurar algumas coisas para que a sua máquina consiga buscar e aceitar o arquivo do servidor fornecedor.


### **Ajustar a sources.list**
--------------------------
Vamos agora ajustar o computador para aceitar software da **packages.ros.org** :

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

### **Ajustar as keys**
--------------------------
Insira o seguinte comando para salvar as keys na máquina, para a instalação:
```
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```

Estas *keys* são chaves para acesso ao repositório do qual instalaremos nossos arquivos. Se você não fizer esta parte, não terá acesso e não conseguirá instalar.


**Respostas esperadas:**
<div align=center>
<img src="https://lh3.googleusercontent.com/pw/ACtC-3c9t5J72-TA8wMdalRwG8_dlZXjazpImfgRrIMRPcGcvO7q7jOpNq1OWrlEp81ZxzNKdQ4xDbuNrVmbJd2C-LE22jtvL2YGq0KnUUkFy5toZuLTBJoTkn-Hc7C7JmCshY5S3ZEemgo3FgAsnBZPZjk=w1274-h669-no?authuser=3" width="800" height="400" />
</div>

<br>

### **Finalmente, a instalação!**
--------------------------

Primeiro, vamos dar um update para ter certeza que está tudo atualizado:
```
sudo apt update
```
Feito isso, vamos instalar o pacote do ROS. **Precisamos** instalar o pacote **"desktop-full"** para instalar os adendos responsáveis por simulação 2D/3D -- como o *Gazebo* -- senão faltarão pacotes na máquina. Assim, o comando é:

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
<img src="https://lh3.googleusercontent.com/pw/ACtC-3cQGWtcaenWvIRceiKe-Uc7R13U7ddaY5XdX2Z9bOMIgYeAZyJsqakBU-iEhuaPwJg_7kZw4kC-VNEAymBxAg5ZfHnUZ0BPcmvBuN6lUTG7LDTRhx648jA1YHnxMGcYWJYszd7kX-S1uE_Hd3pCQm4=w1274-h669-no?authuser=3" width="800" height="400" />
</div>

### **Preparando o "Ambiente"**
--------------------------
É importante configurar o terminal em todo **bash** que se usa ROS.
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
<img src="https://lh3.googleusercontent.com/pw/ACtC-3exhm3PDyOBMMDRGpJpPhkTam21f_Qe9DscdEdtNZNoVgzVGqDTC7j8R80AhRnG9U17PQLvuVB5JeGGil7l7VOLl8LxhMEIUqetVZBKTzjn31fmdQpm9rLukMBo1YUzFVqrd_BIUipvGupIYd0iCcI=w1276-h672-no?authuser=3" width="800" height="400" />
</div>
<br>

## **Como rodar Gazebo + RVIZ e Windows 10 usando WSL2**
Após a instalação, é necessario instalar uma extensão para reproduzir o Gazebo e Rviz
- Baixar:
https://sourceforge.net/projects/vcxsrv/

Após baixar a extensão

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
<div align=center>
<a href="http://www.youtube.com/watch?feature=player_embedded&v=DW7l9LHdK5c
" target="_blank"><img src="http://img.youtube.com/vi/DW7l9LHdK5c/0.jpg" 
alt="link vídeo" width="350" height="300" border="10" /></a>
</div>






 