---
layout: default
title: O que é?
parent: Sobre ROS
nav_order: 1
---
# **Introdução a ROS**

<img src="../assets/img/ros_logo.png" alt="ROS_logo" height="341" width="1280">

## **O que é ROS?**

O ROS (Robot Operating System) é um framework para desenvolvimento, reuso e compartilhamento de software no contexto de robótica.

### **O que é um framework?**

Framework é um conjunto de bibliotecas e estruturas padronizadas que podem ser reutilizadas em diferentes processos. Ou seja, sua principal função é resolver os problemas frequentes, por meio de uma abordagem genérica. Dessa forma, o usuário pode focar no desenvolvimento de algo novo, não tendo que reinventar a roda.

Portanto, o ROS possui ferramentas, bibliotecas e convenções que visam simplificar a tarefa de criar robôs.

## **Conceitos básicos**

Nesta parte serão explicados alguns conceitos básicos do ROS.

### **Node**

Menor unidade de processos executáveis, ou seja a unidade mínima de um projeto no ROS. Um node é um pedaço de código que realiza uma determinada tarefa. Cada node transmite e recebe informações por meio da message.

### **Package**

Principal unidade de organização do software no ROS e é composto de um ou mais nodes, informações para execução dos nodes, entre outros. O package é a menor unidade de construção e lançamento do ROS.

### **Message**

Forma de comunicação entre nodes. A message possui dados que fornecem informações para outros nodes.

### **Topic**

Canal de comunicação entre nodes e identifica o conteúdo da message.

Quando um node está enviando dados, dizemos que está publicando um topic, ou seja, ele é o publisher. Já quando um node está recebendo dados, ele está assinando um topic, ou seja, ele é o subscriber. Vale dizer que os topics podem ter vários subscribers, mas somente um publisher

### **Master**

Núcleo do ambiente em ROS e sabe o que está acontecendo em todo o sistema. É responsável por inicializar o sistema e fornecer o registro de nomes e o serviço de pesquisa para os nodes. Além disso, ela também configura as conexões entre os nodes.

### **Esquema com os conceitos apresentados**

<img src="../assets/img/ROSGazebo/ROS_concepts.jpeg" alt="ROS_concepts" height="385" width="863">

## **Referências**
- http://wiki.ros.org/ROS/Introduction
- http://wiki.ros.org/ROS/Concepts 