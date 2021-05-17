---
layout: default
title: Por que usar ferramentas de simulação?
parent: Sobre o Gazebo
nav_order: 2
---

# **Por que usar ferramentas de simulação?**

Existem diversos tipos de simulação, seja na área da mecânica e até mesmo no setor financeiro, mas todos têm algo em comum: a possibilidade de realizar testes prévios de modo virtual antes do projeto real ser feito. Esse aspecto é muito importante porque permite tomar decisões caso algo não esteja nos conformes ou até mesmo possa estar gerando situações críticas. Por exemplo, é mais viável realizar uma simulação de uma hélice de usina eólica do que precisar modificar a hélice, tendo que construir novamente, após erros que poderiam ser previstos com simulação.

No campo da engenharia mecânica, programas do tipo CAE (Computer-aided engineering) (e.g. Abaqus e Ansys), são muito utilizados para analisar diferentes características de uma peça em regime de trabalho, como o estresse, a deformação, a transferência de calor ou mesmo a distribuição do campo magnético.
Tomando a imagem a seguir como exemplo, é possível ver os níveis de deformação plástica de uma peça mediante impacto. Os resultados são destacados pela cor, sendo que a parte cinza possui maior chance de quebrar e as partes azuis representam as regiões menos afetadas. Dessa forma, podemos analisar qual o comportamento esperado para a peça antes mesmo que ela seja fabricada, de modo que podemos reforçar regiões mais afetadas ou mesmo retirar material das partes menos afetadas
 
<img src="../assets/img/ROSGazebo/simulation_tools_example.jpeg" alt="Simulation_example" height="500" width="auto" style ="margin:auto; display:block">

Analisando o papel do ROS e do Gazebo no projeto de carrinho seguidor de linha, é possível analisar se as dimensões estão adequadas ao tamanho da pista, bem como às curvaturas presentes na mesma, e se o comportamento do carrinho é o desejado, permitindo modificações tanto no código da programação quanto no CAD (Computer-aided design) o que é mais simples e viável do que mudar um projeto físico sem simulação prévia, demonstrando assim que as simulações são muito importantes e não são perda de tempo.
