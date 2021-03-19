# Instalando o ROS/Gazebo em sua máquina Ubuntu

Neste tutorial, vamos aprender a **instalar** o software chamado **ROS** em sua máquina. Junto com ele, vem o ambiente de simulação **Gazebo**, que permite com que você faça o seu robôzinho andar por aí.
Se quiser aprender mais sobre os softwares e para que servem, veja os documentos explicativos (o que é? / porque usar?) sobre cada software - com certeza vai iluminar melhor a questão.

Se você está utilizando Windows e WSL, você está lendo o artigo errado. ***[Clique aqui](../InstalationGuides/ROSGazeboWSL.md)*** para se redirecionar.

<br>
<br>

---
## **Índice**


- [**O que vamos usar?**](#O-que-vamos-usar?)
- [**Habilitando repositórios**](#Habilitando-repositórios)
- [**Ajustar a sources.list**](#Ajustar-a-sources.list)
- [**Ajustar as keys**](#Ajustar-as-keys)
- [**Finalmente, a instalação!**](#Finalmente,-a-instalação!)
- [**Preparando o "Ambiente"**](#Preparando-o-"Ambiente")

---
<br>
<br>

## O que vamos usar? 
---
Grande parte do tutorial vai utilizar o prompt de comando. Para abrir o terminal, você precisa saber qual sistema operacional está sendo utilizado:
- Ubuntu: busque um programa chamado **"Terminal"** ;

![Opening Terminal](/assets/gif/ROSGazebo/openingterminal.gif)

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

Vamos agora dar um enfoque em como instalar este software em Ubuntu.

## **Habilitando Repositórios**
---

Primeiramente, para instalar ROS em Ubuntu, precisamos configurar os **repositórios Ubuntu** para permitir *"restricted", "universe", e "multiverse"*. Podemos fazer isso com os seguintes comandos:

```
sudo add-apt-repository restricted
sudo add-apt-repository universe
sudo add-apt-repository multiverse
sudo apt update
```
A resposta para esses comandos deve ser essa:

![Add Repositories](/assets/img/ROSGazebo/add_repository.png)

Esses comandos permitem com que a sua máquina obtenha arquivos de diferentes tipos de repositório.

Mas o que é um repositório?

Sucintamente, um repositório é um **servidor** que contém diversos **pacotes**, isto é, arquivos e programas, que estão disponibilizados para usuários instalarem em suas máquinas. No entanto, a configuração inicial do Ubuntu é de permitir a entrada de arquivos oriundos de determinados tipos de repositórios.

Em nosso caso, para instalar ROS precisamos de acesso a estes servidores, e por isso inserimos estes comandos.

Segue uma tabela que ajuda a entender de maneira simplificada a diferença entre os repositórios.

\                       | Software Open Source    | Software Não Open Source 
--- | --- | ---
**Recebe Suporte da Canonical**      | Main              | Restricted
**Não Recebe Suporte da Canonical**  | Universe          | Multiverse

<br>
Para saber mais detalhes, leia mais em: 

<https://help.ubuntu.com/community/Repositories>

<br>

Em seguida, vamos configurar algumas coisas para que a sua máquina consiga buscar e aceitar o arquivo do servidor fornecedor.

## **Ajustar a sources.list**
--------------------------
Vamos agora ajustar o computador para aceitar software da **packages.ros.org** :

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
Não se preocupe se o terminal não responder nada depois deste comando -- ele realmente não dá nenhum sinal de que o comando foi feito de maneira correta. Na verdade, se não apareceu nada, você provavelmente fez tudo certo.

## **Ajustar as keys**
--------------------------
Insira o seguinte comando para salvar as *keys* em sua máquina para a instalação:
```
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```

O output esperado desse comando é o seguinte:

![Changing Keys](/assets/gif/ROSGazebo/changing_keys.gif)

Estas *keys* são chaves para acesso ao repositório do qual instalaremos nossos arquivos. Se você não fizer esta parte, não terá acesso e não conseguirá instalar.

## **Finalmente, a instalação!**
---

Primeiro, vamos dar um update para "lavar as mãos" e ter certeza que está tudo atualizado:
```
sudo apt update
```
Feito isso, vamos instalar o pacote do ROS. **Precisamos** instalar o pacote **"desktop-full"** para instalar os adendos responsáveis por simulação 2D/3D -- como o *Gazebo* -- senão faltarão pacotes na máquina. Assim, o comando é:

```
sudo apt install ros-noetic-desktop-full
```
Este comando deve instalar o ROS e o Gazebo juntos. A mensagem de output deve ser semelhante a essa:

![Installing ROS](/assets/gif/ROSGazebo/installing_ros.gif)

Note que, no meio da execução, o terminal pergunta **"Do you want to continue? [Y/n]"**.
Para continuar, basta escrever **y** e apertar Enter.
Neste caso também, se você não escrever nada, e somente pressionar Enter, a resposta default é "Yes", então você também pode fazer isso.

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

## **Preparando o "Ambiente"**
---
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

Após preparar o ambiente, você estará pronto para utilizar o *software* em qualquer momento. Bom proveito!