---
layout: default
title: WSL
parent: Guias de Instalação
nav_order: 1
---

# Instalando o WSL na sua máquina Windows!
![WSL + UBUNTU Logo](../assets/img/WSL/Windows_WSL.jpg)

Olá alunos!

Neste tutorial, vamos aprender a **instalar** o **WSL**, abreviação de *Windows Subsystem for Linux*, no seu PC. Basicamente é uma camada de compatibilidade pra rodar um ambiente de Linux, direto do sistema da Microsoft. Isso traz uma facilidade para o uso e também deixa você continuar no ambiente Windows. Você vai poder rodar todos os comandos e programas específicos ao Linux sem ter que realmente realizar uma instalação completa dele em um pedaço do seu HD. Se quiser saber mais, sinta-se a vontade de perguntar para os monitores e conferir a [pá<<<<<<< feature/whyROS
8
 
gina de documentação oficial da Microsoft sobre o assunto](https://docs.microsoft.com/en-us/windows/wsl/about).

### O que vamos usar?

O tutorial em grande parte vai ser praticamente só navegar pelos muitos menus presentes no Windows. Tudo que você precisa para ativar o WSL e ter uma instalação de Ubuntu no seu PC já está aí, só precisamos encontrar!

Todas as imagens vão mostrar uma instalação em Português do Windows, com os nomes de coisas importantes escritos em **negrito**. Ao lado, ficará a tradução para Inglês em *itálico*.

Primeiramente, você vai ter que habilitar o WSL no Windows. Para isso abra a janela de **Configurações**/*Settings*.

![Opening Settings](../assets/img/WSL/WSL_Configuracoes.png)

Então, clique em **Aplicativos**/*Apps*.

![Opening Apps](../assets/img/WSL/WSL_Apps.png)

Em seguida, na lateral direita, logo abaixo de **Configurações relacionadas**/*Related settings*, clique em **Programas e Recursos**/*Programs and Features*.

![Opening Features](../assets/img/WSL/WSL_Features.png)

Nesta nova tela, encontre e clique na opção **Ativar ou desativar recursos do Windows**/*Turn Windows features on or off*, na lateral esquerda.

![Opening Windows Features](../assets/img/WSL/WSL_Windows_Features.png)

Em seguida, coloque um check na caixinha escrito **Subsistema do Windows para Linux**/*Windows Subsystem for Linux*. Então clique em OK, aguarde as alterações e reinicie seu computador para aplicar as modificações.

![WSL Enable](../assets/img/WSL/WSL_Enable.png)

Para facilitar, no gif a seguir temos o processo inteiro que você deve realizar (ele foi editado pra ficar mais curto então não se espantem se demorar na tela final):

![WSL Complete](../assets/gif/WSL/Complete1.gif)

Com o PC devidamente reiniciado chegamos na parte mais fácil do tutorial, instalar sua distribuição de Linux. Para isso é preciso abrir a **Microsoft Store**.

![Opening Microsoft Store](../assets/img/WSL/WSL_Store.png)

Agora diretamente na barra de pesquisa procure por "Linux" e escolha uma distribuição para instalar na sua máquina. Para essa disciplina vamos usar o [Ubuntu 20.04 LTS](https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6?activetab=pivot:overviewtab).

![Opening Linux Search](../assets/img/WSL/WSL_Store_Search.png)

Abrindo a página do Ubuntu 20.04 LTS, caso você nunca tenha baixado, é só apertar no botão **Obter**/*Get* e fazer o login com sua conta da Microsoft para adquirir a distribuição.

![Opening Ubuntu Page](../assets/img/WSL/WSL_Store_Ubuntu.png)

Com a distribuição obtida, agora é só instalar como se fosse um app normal de celular. Aperte o botão **Instalar**/*Install* e aguarde o processo.

![Opening Ubuntu Install](../assets/img/WSL/WSL_Store_Ubuntu_Install.png)

Finalizada a instalação, aperte no botão **Iniciar**/*Launch* para rodar o Ubuntu pela primeira vez. Você também pode abrir pelo menu iniciar. Deve ser o primeiro programa que aparece.

![Opening Ubuntu Installed](../assets/img/WSL/WSL_Installed.png)

Agora, depois de abrir e aguardar a primeira instalação, você tem que escolher o nome de usuário para a distribuição na linha "Enter new UNIX username". Ele não precisa ser o mesmo da sua máquina Windows mas tem que ser todo em letras minúsculas.

![Opening Ubuntu First Time](../assets/img/WSL/WSL_First_Open.png)

Com um nome de usuário, agora é apenas colocar o sua senha na linha "Enter new UNIX password" e escrever ela de novo em seguida para confirmar.

![Install Finished](../assets/img/WSL/WSL_Finished.png)

E acabou!

Agora que você tem o WSL com Ubuntu 20.04 instalado na sua máquina você pode tirar proveito dos softwares que rodam no Linux, como o ROS/Gazebo, usados na disciplina. Para aprender como instalar eles é só ***[clicar aqui](../InstalationGuides/ROSGazeboWSL.md)*** e seguir as instruções.

### Atualizando para o WSL2

Essa parte do tutorial só é necessária caso você opte por utilizar o Docker para executar seus projetos. Esta parte só é possível para usuários do Windows 10.

Primeiramente, você deve verificar se o seu Windows está atualizado. Para isso abra a janela de **Configurações**/*Settings*, e clique em **Atualização e Segurança**/*Update & Security*.

![Windows Update Settings](/assets/gif/WSL/WSL_set_windowsatt.gif)

Depois disso, vá em *Windows Update*. Caso existam atualizações para fazer, execute-as e reinicie seu computador. Caso contrário, continue neste tutorial.

![Windows Update](/assets/img/WSL/windowsupdated.png)

Agora, é preciso habilitar o recurso de Máquina virtual. Para isso, abra o **prompt de comando**/*command prompt* como administrador e copie a seguinte linha de código:

```
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

![Prompt de comando como ADMIN](/assets/gif/WSL/WSL2_prompt.gif)

Após isso, **reinicie** seu computador.

Agora, você terá que baixar o pacote de atualização do kernel do Linux mais recente. Para isso, baixe o executável disponível **[neste link](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)**. Abra o programa e permita as permissões elevadas.

![GIF kernerl instalation](/assets/gif/WSL/WSl_update.gif)

Por fim, basta definir o WSL2 como a sua versão padrão do WSL. Para isso, abra novamente o **prompt de comando**/*command prompt* como administrador e execute a seguinte linha de código:

```
wsl --set-default-version 2
```

![Set to WSL2](/assets/gif/WSL/set_wsl2.gif)

Pronto! Agora seu WSL está atualizado para o WSL2
___
Se tiver qualquer dúvida, sinta-se a vontade de falar com um dos monitores.

Que o ambiente Linux seja muito receptivo!
