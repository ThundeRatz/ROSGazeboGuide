# Instalando o ROS/Gazebo em sua máquina
![ROS Logo](/assets/img/thunder_ros.png)

Olá alunos!
Neste tutorial, vamos aprender a **instalar** o software chamado **ROS** em sua máquina. Junto com ele, vem o ambiente de simulação **Gazebo**, que permite com que você faça o seu robôzinho andar por aí.
Se quiser aprender mais sobre os softwares e para que servem, veja os documentos explicativos (o que é? / porque usar?) sobre cada software - com certeza vai iluminar melhor a questão.

### O que vamos usar?

Grande parte do tutorial vai utilizar o prompt de comando. Para abrir o terminal, você precisa saber qual sistema operacional está sendo utilizado:
- Ubuntu: busque um programa chamado **"Terminal"** ;
![Opening Terminal](/assets/gif/ROSGazebo/openingterminal.gif)
- Windows: busque um programa chamado **"cmd"**.
![Opening CMD](/assets/img/ROSGazebo/opencmd.png)

Após abrir o terminal, você poderá inserir comandos que vão realizar tarefas para você. Quem mexe em Ubuntu trabalha muito com isso, já que é a maneira principal de se instalar coisas nesse sistema operacional.

Utilizaremos esses comandos como ferramenta principal para a instalação deste software.
O formato para escrever um comando será o seguinte:
```
comando-a-inserir
```
Então, toda caixinha que você encontrar nesse formato, saiba que é um comando a ser inserido.

Após inserir um comando é esperado que ele responda com algumas saídas. Assim, para o comando:

```
gazebo -version
```
O terminal responderá da seguinte forma **se você tiver o Gazebo instalado**:
![Checking Gazebo](/assets/gif/ROSGazebo/gazebo-version.gif)

Como esse comando só tem essa resposta quando o Gazebo estiver apropriadamente instalado, utilize-o no final deste tutorial para ter certeza que fez tudo de maneira correta!

## **Como Instalar ROS/Gazebo em Ubuntu**
--------------------------

Vamos agora dar um enfoque em como instalar este software em Ubuntu.

### **Habilitando Repositórios**
--------------------------

Primeiramente, para instalar ROS em Ubuntu, precisamos configurar os **repositórios Ubuntu** para permitir *"restricted", "universe", e "multiverse"*. Podemos fazer isso com os seguintes comandos:

```
sudo add-apt-repository restricted
sudo add-apt-repository universe
sudo add-apt-repository multiverse
sudo apt update
```
A resposta para esses comandos deve ser essa:

![Opening CMD](/assets/img/ROSGazebo/add_repository.png)

Esses comandos permitem com que o seu comando **apt** consiga baixar arquivos de fontes mais "alternativas". Existem os programas canônicos que podem ser baixados do repositório **main**, mas para a instalação do ROS, precisamos habilitar os repositórios **universe** (software de graça e Open Source para qual o Ubuntu não fornece atualizações de segurança), **multiverse** (que contém software que não é de graça ou Open Source ~~mas baixamos mesmo assim~~) e **restricted** (que contém drivers com proprietários).

Em suma, utilizamos este comando para que o Ubuntu tenha as permissões corretas para instalar o que queremos.

Em seguida, vamos configurar algumas coisas para que a sua máquina consiga buscar e aceitar o arquivo do servidor fornecedor.

### **Ajustar a sources.list**
--------------------------
Vamos agora ajustar o computador para aceitar software da **packages.ros.org** :

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
Não se preocupe se o terminal não responder nada depois deste comando -- ele realmente não dá nenhum sinal de que o comando foi feito de maneira correta. Na verdade, se não apareceu nada, você provavelmente fez tudo certo.

### **Ajustar as keys**
--------------------------
Insira o seguinte comando para "setar" as keys para a instalação:
```
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```

O output esperado desse comando é o seguinte:

![Changing Keys](/assets/gif/ROSGazebo/changing_keys.gif)

Na minha máquina, as keys ficaram "unchanged" (inalteradas, em inglês) pois já tinha instalado ROS anteriormente. Logo, as minhas keys já estavam corretas. Na sua máquina provavelmente a saída deve ser um pouco diferente, mas próxima desta.

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
Este comando deve instalar o ROS e o Gazebo juntos. A mensagem de output deve ser semelhante a essa:

![Installing ROS](/assets/gif/ROSGazebo/installing_ros.gif)

Eu cortei o .GIF no meio, pois a instalação geralmente demora alguns minutos (e um gif de minutos seria grande demais para carregar). Note que, no meio da execução, o terminal pergunta **"Do you want to continue? [Y/n]"**.
Para continuar, basta escrever **y** e apertar Enter.

Ao final da execução, tudo deve ter sido instalado da maneira correta. Para testar, vamos utilizar o mesmo comando do início do tutorial:

```
gazebo -version
```

No terminal, a mensagem deve ser semelhante a essa:

![All done](/assets/img/ROSGazebo/all_done.png)

Agora, se você preferir fazer um teste mais elaborado, tente rodar o comando:

```
gazebo
```
Este comando deve abrir o ambiente de simulação **Gazebo**, da seguinte forma:

![Opening Gazebo](/assets/gif/ROSGazebo/opening_gazebo.gif)

Muito legal, não?

Tendo feito tudo isso, podemos também instalar pacotes específicos diretamente por meio do seguinte comando:
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
Siga os mesmo passos da instalação do ROS/Gazebo no ubuntu

## Como rodar Gazebo + RVIZ e Windows 10 usando WSL2
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
<a href="http://www.youtube.com/watch?feature=player_embedded&v=DW7l9LHdK5c
" target="_blank"><img src="http://img.youtube.com/vi/DW7l9LHdK5c/0.jpg" 
alt="link vídeo" width="240" height="180" border="10" /></a>







 