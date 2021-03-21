# Instalando o ROS/Gazebo em sua máquina Ubuntu

Neste tutorial, vamos aprender a **instalar** o framework chamado **ROS** em sua máquina. Junto com ele, vem o simulador **Gazebo**, que permite com que você faça o seu robôzinho andar por aí.
Se quiser aprender mais e entender para que servem ROS e Gazebo, veja os documentos explicativos (o que é? / porque usar?) sobre cada um deles - com certeza vai iluminar melhor a questão.

Se você está utilizando Windows e WSL, você está lendo o artigo errado. ***[Clique aqui](../InstalationGuides/ROSGazeboWSL.md)*** para se redirecionar.

## **Índice**

- [Instalando o ROS/Gazebo em sua máquina Ubuntu](#instalando-o-rosgazebo-em-sua-máquina-ubuntu)
  - [**Índice**](#índice)
  - [**O que vamos usar?**](#o-que-vamos-usar)
  - [**Habilitando Repositórios**](#habilitando-repositórios)
  - [**Ajustar a sources.list**](#ajustar-a-sourceslist)
  - [**Ajustar as keys**](#ajustar-as-keys)
  - [**Finalmente, a instalação!**](#finalmente-a-instalação)
  - [**Toques finais**](#toques-finais)

## **O que vamos usar?** 

Grande parte do tutorial vai utilizar o prompt de comando. Para abrir o terminal, você precisa saber qual sistema operacional está sendo utilizado:
- Ubuntu: busque um programa chamado **"Terminal"** ;

![Opening Terminal](/assets/gif/ROSGazebo/openingterminal.gif)

Após abrir o terminal, você poderá inserir comandos que vão realizar tarefas para você. Quem mexe em Ubuntu trabalha muito com isso, já que é a maneira principal de se instalar coisas nesse sistema operacional.

Utilizaremos esses comandos como ferramenta principal para a instalação deste software.
O formato para escrever um comando será o seguinte:
```bash
comando-a-inserir
```
Então, toda caixinha que você encontrar nesse formato, saiba que é um comando a ser inserido.

Após inserir um comando é esperado que ele responda com algumas saídas. Assim, para o comando:

```bash
gazebo -version
```
O terminal responderá da seguinte forma **se você tiver o Gazebo instalado**:

![Checking Gazebo](/assets/gif/ROSGazebo/gazebo-version.gif)

Como esse comando só tem essa resposta quando o Gazebo estiver apropriadamente instalado, utilize-o no final deste tutorial para ter certeza que fez tudo de maneira correta!

Vamos agora dar um enfoque em como instalar este software em Ubuntu.

## **Habilitando Repositórios**

Primeiramente, para instalar ROS em Ubuntu, precisamos configurar os **repositórios Ubuntu** para habilitar os repositórios *"restricted", "universe", e "multiverse"*. Podemos fazer isso com os seguintes comandos:

```bash
sudo add-apt-repository restricted
sudo add-apt-repository universe
sudo add-apt-repository multiverse
sudo apt update
```
A resposta para esses comandos deve ser essa:

![Add Repositories](/assets/img/ROSGazebo/add_repository.png)

Esses comandos permitem com que a sua máquina obtenha arquivos de diferentes tipos de repositório.

Mas o que é um repositório?

Sucintamente, um repositório é um **servidor** que contém diversos **pacotes**, isto é, arquivos e programas, que estão disponibilizados para usuários instalarem em suas máquinas. Por padrão, o Ubuntu não habilita o acesso aos repositórios restricted, universe e multiverse mas para instalar o ROS precisamos de acesso a esses servidores.

Em nosso caso, para instalar ROS precisamos de acesso a estes servidores, e por isso inserimos estes comandos.

Para saber mais sobre as diferenças dos repositórios, acesse o link:
<https://help.ubuntu.com/community/Repositories>

Em seguida, vamos configurar algumas coisas para que a sua máquina consiga buscar e aceitar o arquivo do servidor fornecedor.

## **Ajustar a sources.list**

Vamos agora ajustar o computador para aceitar pacotes do **repositório do ROS** :

```bash
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
Não se preocupe se o terminal não responder nada depois deste comando -- ele realmente não dá nenhum sinal de que o comando foi feito de maneira correta. Na verdade, se não apareceu nada, você provavelmente fez tudo certo.

## **Ajustar as keys**

Insira o seguinte comando para salvar as chaves do repositório do ROS na sua máquina:

```bash
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```

O output esperado desse comando é o seguinte:

![Changing Keys](/assets/gif/ROSGazebo/changing_keys.gif)

As chaves são necessárias para acesso ao repositório do ROS, do qual instalaremos nossos arquivos. Se você não fizer esta parte, não terá acesso à ele e não conseguirá instalar.

## **Finalmente, a instalação!**

Primeiro, vamos rodar um comando para atualizar o sistema com as modificações que fizemos até agora:

```bash
sudo apt update
```
Feito isso, vamos instalar o pacote do ROS. **Precisamos** instalar o pacote **"desktop-full"** para instalar os adendos responsáveis por simulação 2D/3D -- como o *Gazebo* -- senão faltarão pacotes na máquina. Assim, o comando é:

```bash
sudo apt install ros-noetic-desktop-full
```
Este comando deve instalar o ROS e o Gazebo juntos. A mensagem de output deve ser semelhante a essa:

![Installing ROS](/assets/gif/ROSGazebo/installing_ros.gif)

Note que, no meio da execução, o terminal pergunta **"Do you want to continue? [Y/n]"**.
Para continuar, basta escrever **y** e apertar Enter.
Neste caso também, se você não escrever nada, e somente pressionar Enter, a resposta default é "Yes", então você também pode fazer isso.

Ao final da execução, tudo deve ter sido instalado da maneira correta. Para testar, vamos utilizar o mesmo comando do início do tutorial:

```bash
gazebo -version
```

No terminal, a mensagem deve ser semelhante a essa:

![All done](/assets/img/ROSGazebo/all_done.png)

Agora, se você preferir fazer um teste mais elaborado, tente rodar o comando:

```bash
gazebo
```
Este comando deve abrir o ambiente de simulação **Gazebo**, da seguinte forma:

![Opening Gazebo](/assets/gif/ROSGazebo/opening_gazebo.gif)

Muito legal, não?

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

Rodar esse comando manualmente sempre pode se tornar trabalhoso. Como nós somos pessoas preguiçosas, configuramos o sistema para fazer isso automaticamente.

A maneira de fazer isso é a seguinte:

```bash
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

O que esse comando faz é adicionar a linha de texto `source /opt/ros/noetic/setup.bash` para o arquivo `.bashrc`. Este arquivo contém uma lista de comandos que são executados toda vez que um novo terminal é aberto. Dessa forma, você não precisa escrever o mesmo comando sempre.

Após preparar o ambiente, você estará pronto para utilizar o *software* em qualquer momento. Bom proveito!