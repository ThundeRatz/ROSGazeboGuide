---
layout: default
title: O que é?
parent: Sobre ROS
nav_order: 1
---
# **Introdução a ROS**

<img src="../assets/img/ros_logo.png" alt="ROS_logo" height="341" width="1280">

## **Índice**<!-- omit in toc -->
- [**O que é ROS?**](#O-que-é-ROS?)
    - [**O que é um framework**](#O-que-é-um-framework)
- [**Conceitos básicos**](#Conceitos-básicos)
    - [**Node**](#**Node**)
    - [**Package**](#**Package**)
    - [**Message**](#**Message**)
    - [**Topic**](#**Topic**)
    - [**Master**](#**Master**)
    - [**Esquema com os conceitos apresentados**](#Esquema-com-os-conceitos-apresentados)
- [**Referências**](#Referências)

## **O que é ROS?**

Imagine que você está construindo um robô e ele possui diferentes módulos, tais como câmeras, sensores, e eles precisam comunicar entre si. Aí você se pergunta: teria uma forma de facilitar essa comunicação? Bem, a resposta é sim, usando o ROS! 

O Robot Operating System (ROS) é um framework para desenvolvimento, reuso e compartilhamento de software no contexto de robótica. 

### **O que é um framework?**

Framework é um conjunto de bibliotecas e estruturas padronizadas que podem ser reutilizadas em diferentes processos. Ou seja, sua principal função é resolver os problemas frequentes, por meio de uma abordagem genérica. Dessa forma, o usuário pode focar no desenvolvimento de algo novo, não tendo que reinventar a roda.
Um exemplo disso é o uso do React, que fornece as funcionalidades e as estruturas para a programação de páginas web complexas, a partir de um conjunto de funcionalidades padrões que permitem a criação de projetos. Aliás, um framework pode ser feito a partir de uma coleção de padrões, APIs e até mesmo de bibliotecas.

Mas por que usar um framework?
Bem, eles permitem algumas vantagens, como

- Redução na incidência de bugs
- Padronização de códigos
- Redução de custos operacionais
- Maior consistência das aplicações

Portanto, o ROS possui ferramentas, bibliotecas e convenções que visam simplificar a tarefa de criar robôs.

## **Conceitos básicos**

Para criar um robô com o ROS, diversos fatores devem ser levados em conta, como a comunicação dele com o código, as tarefas que ele deverá executar, entre outras coisas. Nesta parte serão explicados alguns conceitos essenciais do ROS. 

### **Node**

Menor unidade de processos executáveis, ou seja a unidade mínima de um projeto no ROS. Um node é um pedaço de código que realiza uma determinada tarefa. Cada node transmite e recebe informações por meio da message. Para saber mais detalhadamente sobre o que são nodes, dê uma olhada na Wiki oficial do ROS, disponível [**nesse link**](http://wiki.ros.org/Nodes).

### **Package**

Principal unidade de organização do software no ROS e é composto de um ou mais nodes, informações para execução dos nodes, entre outros. O package é a menor unidade de construção e lançamento do ROS. Para saber mais detalhadamente sobre o que são nodes, dê uma olhada na Wiki oficial do ROS, disponível [**nesse link**](http://wiki.ros.org/Packages).

### **Message**

Forma de comunicação entre nodes. A *message* possui dados que fornecem informações para outros nodes.

### **Tópico**

Canal de comunicação entre nodes e identifica o conteúdo da message.

Quando um node está enviando dados, dizemos que está publicando um tópico, ou seja, ele é o publisher. Já quando um node está recebendo dados, ele está assinando um tópico, ou seja, ele é o subscriber. Vale dizer que os tópicos podem ter vários subscribers, mas somente um publisher

Para saber mais detalhadamente sobre o que são tópicos, dê uma olhada na Wiki oficial do ROS, disponível [**nesse link**](http://wiki.ros.org/Packages).
### **Master**

Núcleo do ambiente em ROS e sabe o que está acontecendo em todo o sistema. É responsável por inicializar o sistema e fornecer o registro de nomes e o serviço de pesquisa para os nodes. Além disso, ela também configura as conexões entre os nodes.

### **Esquema com os conceitos apresentados**

<img src="../assets/img/ROSGazebo/ROS_concepts.jpeg" alt="ROS_concepts" height="385" width="863">

Explicando a imagem: 

## **Referências**
- http://wiki.ros.org/ROS/Introduction
- http://wiki.ros.org/ROS/Concepts 