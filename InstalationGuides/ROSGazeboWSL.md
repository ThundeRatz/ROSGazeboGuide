# Instalando o ROS/Gazebo em sua máquina

Neste tutorial, vamos aprender a **instalar** o software chamado **ROS** em sua máquina. Junto com ele, vem o ambiente de simulação **Gazebo**, que permite com que você faça o seu robôzinho andar por aí.
Se quiser aprender mais sobre os softwares e para que servem, veja os documentos explicativos (o que é? / porque usar?) sobre cada software - com certeza vai iluminar melhor a questão.

Vamos, neste documento, dar um enfoque a como instalar ROS/Gazebo no Windows com WSL.

Se você está utilizando Ubuntu, você está lendo o artigo errado. ***[Clique aqui](../InstalationGuides/ROSGazeboUbuntu.md)*** para se redirecionar.

<br>

---

<br>

## Índice


- [**Habilitando Repositórios**](#habilitando-repositórios)
- [**Ajustar a sources.list**](#ajustar-a-sources.list)
- [**Ajustar as keys**](#ajustar-as-keys)
- [**Finalmente, a instalação!**](#finalmente-a-instalação!)
- [**Preparando o "Ambiente"**](#preparando-o-"ambiente")
- [**Instruções para pós instalação**](#Instruções-para-pós-instalação)

<br>

---

<br>

## **Como Instalar ROS/Gazebo em WSL**

Os passos da instalação do ROS/Gazebo são similares ao Ubuntu sem o WSL:

Abra o terminal do Ubuntu no Windows



![abertura ubuntu](../assets/gif/ROSGazebo/WSL/0_opening_ubuntu.gif)

<br>

## **Habilitando Repositórios**


Primeiramente, para instalar ROS no Ubuntu em WSL, precisamos configurar os **repositórios Ubuntu** para permitir *"restricted", "universe", e "multiverse"*. Podemos fazer isso com os seguintes comandos:

```
sudo add-apt-repository restricted
sudo add-apt-repository universe
sudo add-apt-repository multiverse
sudo apt update
```
**Resposta esperada:**
![configurando repositório](../assets/gif/ROSGazebo/WSL/1_repositories.gif)


Esses comandos permitem com que a sua máquina obtenha arquivos de diferentes tipos de repositório.

Mas o que é um repositório?

Sucintamente, um repositório é um **servidor** que contém diversos **pacotes**, isto é, arquivos e programas, que estão disponibilizados para usuários instalarem em suas máquinas. No entanto, a configuração inicial do Ubuntu é de permitir a entrada de arquivos oriundos de determinados tipos de repositórios.

Em nosso caso, para instalar ROS precisamos de acesso a estes servidores, e por isso inserimos estes comandos.

Segue uma tabela que ajuda a entender de maneira simplificada a diferença entre os repositórios.

<br>

\                       | Software Open Source    | Software Não Open Source 
--- | --- | ---
**Recebe Suporte da Canonical**      | Main              | Restricted
**Não Recebe Suporte da Canonical**  | Universe          | Multiverse


Para saber mais detalhes, leia mais em: 

<https://help.ubuntu.com/community/Repositories>

<br>

Em seguida, vamos configurar algumas coisas para que a sua máquina consiga buscar e aceitar o arquivo do servidor fornecedor.

Em seguida, vamos configurar algumas coisas para que a sua máquina consiga buscar e aceitar o arquivo do servidor fornecedor.

<br>

### **Ajustar a sources.list**

Vamos agora ajustar o computador para aceitar software da **packages.ros.org** :

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
<br>

## **Ajustar as keys**

Insira o seguinte comando para salvar as keys na máquina, para a instalação:
```
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```

Estas *keys* são chaves para acesso ao repositório do qual instalaremos nossos arquivos. Se você não fizer esta parte, não terá acesso e não conseguirá instalar.


**Respostas esperadas:**
![configurando key e source](../assets/gif/ROSGazebo/WSL/2_source_key.gif)

<br>

## **Finalmente, a instalação!**


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
![instalação](../assets/gif/ROSGazebo/WSL/3_instalation.gif)

<br>

## **Preparando o "Ambiente"**

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
![ambiente](../assets/gif/ROSGazebo/WSL/4_environment.gif)

<br>

## ***Instruções para pós instalação***

Após preparar o ambiente, a instalação do ROS e do Gazebo estará finalizada!

Mas vamos com calma ainda, amigo. Para utilizar o ROS e suas extensões pelo WSL será necessario instalar o Xserver, que também temos um guia de instalação!


Para instalar o Xserver  ***[clique aqui](../InstalationGuides/XServer.md)***

Depois disso tudo isso, seu windows estará pronto para utilizar corretamente o ROS.

Bom proveito!










 